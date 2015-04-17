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
- Contributing, includes reassignment of copyright

# Services

## Authentication and Authorization

Use the `id.prx.org` for user authentication.
It has the ability to provide plain embeddable iframes, and to skip some interactions for PRX specific sites.

Use the `rack_prx-auth` gem for token based API authentication.
Tokens also include

Use the `pundit` gem for authorization.
Rules can rely on user and account information provided by `id.prx.org` in both responses and tokens.
(TBD) Use the PRX gem for extracting and requesting user account role information.

## Private Data and Secrets

- Use `dotenv-rails` to specify keys and other private data in an `.env` file
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


# Best Practices

These are more likely to change, as they depend on particular tech.

## Development

### Running Locally

We use pow to run web applications and services locally.
This defaults to using the '.dev' TLD for locally running projects.
Add a `.powder` file to specify the domain and subdomain to use with '.dev'.

### Process

1) Create a branch
- Branches should be named using a `feat/` or `fix/` prefix
- After the prefix, add a short unique name all lower case and underscores
- The name should be descriptive of the changes

2) Make changes
- Make changes to the code, commiting at your own pace, but often is good
- Add comments as needed, but code should be as readable as possible
- Add and update tests as needed
- All changes are expected to have working tests
- Each commit should include a non-technical message (release notes worthy)

3) Commit and push changes
- Push the updated branch to the remote origin
- Do not make branches on a user or other fork
  - This allows travis to test the branch and PR
- Remote push will trigger hound and travis tests
- Fix all test failures,

4) Create a Pull Request (PR)
- Create a PR for the branch in github
- Make the title as non-technical as possible (release notes worthy)
- Add description of anything not yet done, or that needs explaining to a reviewer
- Assign the PR to a reviewer when it is complete

5) Code Review
- Reviewer reads the changes, comments on issues or questions
- Author makes changes or answers questions
- When both are satisfied, Reviewer merges changes, and deletes branch

### Tests

All code is expected to have tests, and to have appropriate coverage.
Acceptable coverage is determined by the review, generally expected to be highly covered.

#### Frequently Used Gems:
`minitest-rails` for ruby/rails projects.
`simplecov` for local test coverage
`guard` for testing as you save changes.
`factory-girl` for test data factories
`mocha` for mocking, or just minitest mocks and stubs
`webmock` for remote http calls, if necessary

#### Frequently Used Services:
`coveralls` for code coverage
`travis` for testing
`hound` to check styles

### Upgrades

Gems should be added and updated as needed as part of authoring a PR.

In general, larger updates, such as to Rails, should be made as their own PRs.
