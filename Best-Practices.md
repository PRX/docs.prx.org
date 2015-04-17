These are more subject to change and refinement than standards, but still should be followed when appropriate.

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

## Testing

All code is expected to have tests, and to have appropriate coverage.
Acceptable coverage is determined by the review, generally expected to be highly covered.

### Frequently Used Gems:
`minitest-rails` for ruby/rails projects.
`simplecov` for local test coverage
`guard` for testing as you save changes.
`factory-girl` for test data factories
`mocha` for mocking, or just minitest mocks and stubs
`webmock` for remote http calls, if necessary

### Frequently Used Services:
`coveralls` for code coverage
`travis` for testing
`hound` to check styles

### Upgrades

Gems should be added and updated as needed as part of authoring a PR.

In general, larger updates, such as to Rails, should be made as their own PRs.
