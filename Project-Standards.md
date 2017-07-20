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

### Domains

Deployed PRX projects should be hosted on one (or possibly more if using `.tech`) PRX domains:

- `prx.org` - Normal public-facing PRX services
- `prxu.org` - Hosts all user-generated content, to prevent potentially malicious content from executing under `prx.org` permissions ([same-origin policy](https://en.m.wikipedia.org/wiki/Same-origin_policy)).
- `prx.tech`
  - Internal PRX tools and services
  - Use as a temporary name when setting up or testing a `prx/prxu` setup

Staging services should use a similar name to production, but with a `-staging` after the name (e.g. `cms-staging.prx.org`).  Do _not_ just add another dot to the name, as in `staging.cms.prx.org`, as this won't work with our wildcard certs.  Other named environments should follow this same pattern - `cms-demo.prx.org` or `cms-stress.prx.org`.

### Documentation

Reference these standards in the README so as not to repeat their full explanation.

The following is also required for a web project README.md:
- Badges for travis, coveralls, code climate, and gemnasium
- Description
  - Should include a brief overview of what the application does, and how it fits into the larger PRX architecture. Avoid getting into technical specifics - those can come in a different section, or another file entirely.
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

#### Environment Variables

##### AWS

Historically AWS inconsistently used various environment variables for API and SDK related values. Unless otherwise avoidable, use the following keys to define common values. These are based on the most recent efforts by AWS to [standardize variables](http://blogs.aws.amazon.com/security/post/Tx3D6U6WSFGOK2H/A-New-and-Standardized-Way-to-Manage-Credentials-in-the-AWS-SDKs). Even if a third-party library expects an alternate version of some key, opt for the standard and explicitly passing the value to the library. Avoid defining multiple equivalent values. Avoid prefixing keys for other services that rely on AWS with `AWS_`; scope them to the service they are being defined for (e.g. `CACHE_S3_BUCKET`).

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`
* `AWS_SESSION_TOKEN`
* `AWS_REGION`

##### Database

When possible (i.e. with Postgres databases on Heroku, AWS RDS, etc), use a single `DATABASE_URL` environment variable to define connection settings.

### Monitoring

We use NewRelic for application monitoring, included using the following gems:
```
gem 'newrelic_rpm'
gem 'capistrano-newrelic'
```

A `newrelic.yml` config file should also be included specifying PRX's NewRelic API key.