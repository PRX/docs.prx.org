These are the standards and best practices to be followed so long as they make sense and changed when we figure out a better way.

## Basics

### Repository

- Projects should be stored to the PRX Github organization.
- They should have LICENSE and README.md files at the root.

### Naming

- For an application or service, name the repository with the production domain name
  - e.g. the CMS service runs as 'cms.prx.org', and that is PRX/cms.prx.org on github

- For a gem, use standard gem naming practices with underscores and dashes.
- Add 'prx' to the name only if it is specific to PRX, not just as the source.

### Documentation

Reference these standards in the README so as not to repeat their full explanation.

The following is also required for a web project README.md:
- Badges for travis, coveralls, code climate, and gemnasium
- Description
- Installation
- Integrations and/or dependencies
- Usage
- License
  - use MIT for gems
  - use AGPL for applications and services
- Contributing, includes reassignment of copyright
  - (TBD) boilerplate language that contributing a PR also transfers ownership of code

# Services

## Ruby Version

Specify the version of ruby used for the project using a `.ruby-version` file. The version specified should **exactly match** the version used for the project in production.

## Authentication and Authorization

Use the `id.prx.org` for user authentication.
It has the ability to provide plain embeddable iframes, and to skip some interactions for PRX specific sites.

Use the `rack_prx-auth` gem for token based API authentication.
Tokens also include information about the scopes and account(s) accessible by this token.

Use the `pundit` gem for authorization.
Rules can rely on user and account information provided by `id.prx.org` in both responses and tokens.
(TBD) Use the PRX gem for extracting and requesting user account role information.

## Private Data and Secrets

- Use `dotenv-rails` to specify keys and other private data in an `.env` file for development
- Provide an `env-example` file with all environment variables listed but unassigned
- Add `.env*` to the .gitignore


## API Design

We use the HAL for our APIs, so new APIs should use this if possible (e.g. elastic search doesn't, don't force it).

- Maintain a root document describing available endpoints
- Declare and use curies to meta.prx.org
- (TBD) Add new link relations to meta.prx.org
- Add a HAL Browser to the root of the application (if public)

There are several libraries to help with this:
- For JSON (de)serializing, use the `roar` gem
- (TBD) For representers, use the PRX mixins for embedding and caching
- (TBD) For controllers, use the PRX mixins for HAL actions

## Running in Production

### Deployment

Deployment or production should be possible using a single command.

Most applications are deployed using `capistrano`, though we also `chef` and are experimenting with `docker` on various platforms.


### Monitoring

We use NewRelic for application monitoring, included using the following gems:
```
gem 'newrelic_rpm'
gem 'capistrano-newrelic'
```

A `newrelic.yml` config file should also be included specifying PRX's NewRelic API key.