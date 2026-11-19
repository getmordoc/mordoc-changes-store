# Keep dependencies up to date and editors consistent: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given new versions of Mordoc's packages, when the weekly check runs, then one pull request proposes all minor and patch updates, and each major update has a pull request of its own.
- **AC-002:** Given new versions of the actions in Mordoc's workflows, when the weekly check runs, then one pull request proposes them.
- **AC-003:** Given an update pull request, when it is opened, then the tests run on it like on any other pull request.
- **AC-004:** Given an editor that reads shared settings, when a contributor edits and saves a file, then it uses two spaces for indentation, Unix line endings and ends with an empty line.
- **AC-005:** Given the shared editor settings, when they are compared with Mordoc's files, then every file already follows them.

## Functional Requirements
- **FR-001:** Once a week, Mordoc's packages are checked for new versions, and the updates are proposed as pull requests.
  - Minor and patch updates are proposed together, each major update on its own.
- **FR-002:** Once a week, the actions in Mordoc's workflows are checked for new versions, and the updates are proposed together in one pull request.
- **FR-003:** Editors that read shared settings use the same indentation, line endings and end of file for every file in Mordoc.

## Non-Functional Requirements
- **NFR-001:** Existing files need no changes to follow the shared editor settings.

## Boundaries
- None

## Constraints
- None

## Risks
- A major update can need real work before its pull request can be merged.
- [Version strategy](../chore-version-strategy/proposal.md) also decides when dependencies are updated, and may change the weekly schedule.

## Open Issues
- Confirm that security alerts and security updates are switched on in the repository's settings on GitHub.
