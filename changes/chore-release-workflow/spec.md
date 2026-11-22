# Release Mordoc with one click: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The maintainer can release a new version with one click on GitHub.
- **AC-002:** Users can install the new version from npm.
- **AC-003:** Users can see on GitHub what each version contains.
- **AC-004:** The maintainer sees a release stop before anything is published when something is wrong.
- **AC-005:** After a release, the maintainer gets a branch that raises the minor version, to open a pull request from.

## Functional Requirements
- **FR-001:** A release is started by hand with a "Create release" button on GitHub, runs on the main branch, and uses the version Mordoc has there.
- **FR-002:** A release runs all tests, then publishes the version to npm, then adds its tag and release on GitHub.
- **FR-003:** A release stops before publishing when a test fails, or when the version already exists on npm or GitHub.
- **FR-004:** Every pull request is marked with its type, taken from the start of its branch name: feat, fix, refactor, perf, test, docs or chore.
- **FR-005:** The release notes list every pull request merged since the previous release, grouped by type.
- **FR-006:** After a release, a branch raises the minor version, such as from 2.1.0 to 2.2.0, and resets the patch number to 0.

## Non-Functional Requirements
- **NFR-001:** Publishing to npm needs no password or token stored in GitHub, and npm shows which release and commit each version was built from.
- **NFR-002:** A release takes at most 15 minutes.

## Boundaries
- None

## Constraints
- The main branch changes only through pull requests.

## Risks
- The release notes are only as clear as the pull request titles.
- An owner of the package on npm has to allow publishing from GitHub once.

## Open Issues
- Agree who may start a release.
