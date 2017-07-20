These are more subject to change and refinement than standards, but still should be followed when appropriate.

# Design

## Preconditions
* The general idea, scope, size, and duration for the design should be discussed before starting.
* There should be a github repo and issue(s) tracking the feature, scheduled for a milestone.

## Process
For new apps or large features, follow a Design Thinking process, usually including the following elements, in order, iteratively, and as needed.

1. *Problem statement* - devise an initial problem statement to center things on
1. *User interviews* - talk with the people involved in the problem area to understand more about what they do and what is important
1. *Research* - investigate related trends, existing/competing products, and information on the topic
1. *Point of View* - based on the interviews, write a POV statement to guide the design
1. *Brain Storm Solutions* - with a team, flare with a brain storm of possible solutions, then focus on a smaller number of solutions to pursue
1. *One sheet* - for each chosen possible solution (1-3), create "one sheet" descriptions, discuss and pick favorites
1. *Prototype* - create paper or other rough prototypes, enough to be testable. Show the prototypes to possible users, record feedback, and iterate.
1. *Wireframe* - create digital interactive wireframes (i.e. using sketch and invision), further test internally and with users and iterate on these
1. *Design Review* - review the wireframes with UX and FE leads to make sure it follows standards, is consistent with any other design guides, and for use or expansion of the style guide for the components in the pages


# Development

## Process

### 1. Create a branch
- Branches should be named using a `feat/`, `fix/`, `chore/`, etc prefix
- After the prefix, add a short unique name all lower case and underscores
- The name should be descriptive of the changes

### 2. Make changes
- Make changes to the code, committing at your own pace, but often is good
- Add comments as needed, but code should be as readable as possible
- Add and update tests as needed
- All changes are expected to have working tests
- Each commit should include a non-technical message (release notes worthy)

### 3. Commit and push changes
- Push the updated branch to the remote origin
- Do not make branches on a user or other fork
  - This allows travis to test the branch and PR
- Remote push will trigger hound and travis tests
- Fix all test failures,

### 4. Create a Pull Request (PR)
- Create a PR for the branch in github
- Make the title as non-technical as possible (release notes worthy)
- Add description of anything not yet done, or that needs explaining to a reviewer
- Assign the PR to a reviewer when it is complete
- If you find yourself explaining specific lines of code to the reviewer in the PR, consider moving these comments into the code itself. Otherwise they're just lost after merge.

### 5. Code Review
- Reviewer reads the changes, comments on issues or questions
- Author makes changes or answers questions
- When both are satisfied, Reviewer merges changes, and deletes the branch

## Running Locally

### docker-compose

Most PRX projects include a `Dockerfile` and `docker-compose.yml`.  You should
consider developing/testing via Docker whenever possible, since it gives you an
environment identical to production.

### rbenv

We use rbenv to easily switch between versions of ruby for different apps.
Each web app/service should provide a `.ruby-version` file to work with `rbenv`.

### pow & powder

We use pow to run web applications and services locally.
This defaults to using the '.dev' TLD for locally running projects.
Add a `.powder` file to specify the domain and subdomain to use with '.dev'.


## Upgrades

Gems should be added and updated as needed as part of authoring a PR.

In general, larger updates, such as to Rails, should be made as their own PRs.

# Testing

All code is expected to have tests, and to have appropriate coverage.
Acceptable coverage is determined by the review, generally expected to be highly covered.

## Tools

### Frequently Used Gems:
* `minitest-rails` for ruby/rails projects.
* `simplecov` for local test coverage
* `guard` for testing as you save changes.
* `factory-girl` for test data factories
* `mocha` for mocking, or just minitest mocks and stubs
* `webmock` for remote http calls, if necessary

### Frequently Used Services:
* `coveralls` for code coverage
* `travis` for testing
* `hound` to check PRs
* `code climate` to give overall style and coverage scores

## Integration Testing

Currently implemented for the www app integrating with the cms.  This needs revisiting, especially to include dependencies between services for coordinated releases, and for better repeatable testing with standard test data.
