# Run the tests for every pull request: QA Plan

**Change:** `chore-ci-tests`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- The change adds a workflow only; Mordoc's code and tests are not changed, and `npm test` must keep passing on a contributor's machine.
- The workflow can only be verified on GitHub: push the branch and open a pull request into `main`.

## Test Coverage
- **AC-001:** Open the pull request for this change: the `test` check runs, its log shows the validation tests and the browser tests passing, and the pull request shows the check as passed, within ten minutes.
- **AC-002:** Push a new commit to the pull request: the `test` check runs again on that commit.
- **AC-003:** Push a temporary commit that breaks a test, such as a wrong line in `test/build/errors/expected.txt`: the check fails and its log names the failing test. Remove the commit afterwards.
- **AC-004:** Merge the pull request: the `test` check runs on the merge commit on `main` and passes.
