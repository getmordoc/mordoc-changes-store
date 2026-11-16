# Run the tests for every pull request: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a pull request into `main`, when it is opened, then all tests run and the pull request shows whether they passed.
- **AC-002:** Given an open pull request into `main`, when new commits are pushed to it, then all tests run again on the new code.
- **AC-003:** Given a pull request that breaks a test, when the tests run, then the pull request shows that they failed, and the log names the failing test.
- **AC-004:** Given a pull request that is merged into `main`, when the merge lands, then all tests run on `main`.

## Functional Requirements
- **FR-001:** All tests, the validation tests and the browser tests, run when a pull request into `main` is opened, updated or reopened.
- **FR-002:** All tests run on `main` when something is merged or pushed into it.
- **FR-003:** The result shows on the pull request and on the commit, with a log of each test.

## Non-Functional Requirements
- **NFR-001:** The tests run the same way as on a contributor's machine, with the same command and real internet.
- **NFR-002:** A pull request from a fork can't read secrets or change the repository.
- **NFR-003:** A run finishes within ten minutes.

## Boundaries
- None

## Constraints
- Runs on GitHub Actions, within its free minutes for public repositories.

## Risks
- The embedded videos come from an external service, so a run can fail when that service can't be reached.

## Open Issues
- Should a failing run block merging? That is a branch protection setting on GitHub, set by a maintainer after this change is merged.
