Here are some basic instructions for setting up a build/deploy pipeline for a Docker project:

## Prerequisites

Get everything running in our ECS staging environment, somehow.  You need an existing task/service/elb/etc.

## ENV Variables

Create a new snap project for your repo, with the following, with the following GLOBAL ENVs (you have to click the pin next to them, so they show up for all stages):

UNSECURED:

    ECR_REPO=foobar.prx.org  #usually just match to the github repo name
    AWS_DEFAULT_REGION=us-east-1
    AWS_ACCOUNT_ID=561178107736
    SNAP_API_USER=cavis

SECURED: (these are in LastPass -> Secure Notes -> SnapCI credentials)

    SNAP_API_KEY=???  #this is my key in the preview env - will have to change when we go to prod
    AWS_ACCESS_KEY_ID=???
    AWS_SECRET_ACCESS_KEY=???

## Stage 1: Test

Run your test suite

    # do whatever you need to run your tests
    npm install
    npm test

## Stage 2: Dockerize

Build a docker image and push it to ECR.

    REPO_STRING="$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$ECR_REPO:$SNAP_BRANCH$SNAP_UPSTREAM_BRANCH.$SNAP_PIPELINE_COUNTER"
    echo "Exporting to $REPO_STRING"
    ECR_LOGIN=$(aws ecr get-login)
    eval sudo $ECR_LOGIN
    aws ecr create-repository --repository-name=$ECR_REPO || true
    sudo docker build --tag=$REPO_STRING .
    sudo docker push $REPO_STRING

## Stage 3: Stage

Deploy the image you just built to our ECS staging cluster

    REPO_STRING="$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$ECR_REPO:$SNAP_BRANCH$SNAP_UPSTREAM_BRANCH.$SNAP_PIPELINE_COUNTER"
    curl -sL https://raw.githubusercontent.com/PRX/meta.prx.org/master/bin/ecs-deploy > ecs-deploy
    chmod +x ecs-deploy
    sudo apt-get --assume-yes install jq
    ./ecs-deploy --cluster prx-staging --service-name [name of your ECS service] --image $REPO_STRING --timeout 120

## Stage 4: Trigger

Trigger the meta.prx.org pipeline, which will run acceptance tests against staging, and allow a click-button deploy to production.

    curl -u $SNAP_API_USER:$SNAP_API_KEY -X POST -H 'Accept:application/vnd.snap-ci.com.v1+json' -H 'Content-type:application/json' https://api-preview.snap-ci.com/project/PRX/meta.prx.org/branch/master/trigger --data '{"env":{"PRX_TRIGGER":"$ECR_REPO"}}'

I'm not sure that env-data actually works.  But someday!

Save/run your pipeline.  Edit until it all works.

## Meta repo

Then add some acceptance tests to the meta.prx.org repo.  And in Snap, edit the 2nd "Resolve" stage of the meta.prx.org pipeline to add your ECS service:

    # add these 2 lines, to concat your service to the staging.env file
    SERVICE_FOOBAR=$(./bin/ecs-image --cluster prx-staging --service-name your-service-name-here)
    echo "SERVICE_FOOBAR=$SERVICE_FOOBAR" >> staging.env

When you've also got a prod service setup, add it to the mappings in the 3rd "Deploy_Prod" stage:

    ./bin/deploy-env --cluster prx-production --timeout 150 --mapping "dovetail=$SERVICE_DOVETAIL,yourprodservice=$SERVICE_FOOBAR"

Then... profit.