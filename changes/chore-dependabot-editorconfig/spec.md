# Keep dependencies up to date and editors consistent: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The maintainer gets pull requests that propose updates to Mordoc's packages and workflow actions.
- **AC-002:** The maintainer is warned about security problems in Mordoc's packages, with a fix proposed.
- **AC-003:** Contributors' editors save Mordoc's files the same way.

## Functional Requirements
- **FR-001:** Once a week, Mordoc's packages are checked for new versions. Minor and patch updates are proposed together in one pull request, and each major update in a pull request of its own.
- **FR-002:** Once a week, the actions in Mordoc's workflows are checked for new versions, and their updates are proposed together in one pull request.
- **FR-003:** A known security problem in one of Mordoc's packages is reported, and its fix is proposed in a pull request as soon as it is known.
- **FR-004:** The tests run on every update pull request, and the release notes list updates under maintenance.
- **FR-005:** Editors that read shared settings use two spaces for indentation, Unix line endings and an empty line at the end of every file.

## Non-Functional Requirements
- **NFR-001:** Mordoc's existing files already follow the shared editor settings.

## Boundaries
- None

## Constraints
- None

## Risks
- A major update can need real work before its pull request can be merged.
- [Version strategy](../chore-version-strategy/proposal.md) also decides when dependencies are updated, and may change the weekly schedule.

## Open Issues
- None
