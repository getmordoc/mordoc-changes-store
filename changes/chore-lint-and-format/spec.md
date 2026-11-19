# Lint and format the code: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Contributors can check the code for common mistakes and formatting with one command.
- **AC-002:** Contributors can fix the formatting and simple mistakes with one command.
- **AC-003:** A pull request with a common mistake or unformatted code shows a failing check.
- **AC-004:** Reviewers see only the real changes in a pull request.

## Functional Requirements
- **FR-001:** The check covers every file of Mordoc that the tool supports, including the tests, and finds common mistakes such as unused code, wrong use of React hooks and code that can't work as written.
- **FR-002:** The formatting follows the style most of the code already uses, and the shared editor settings.
- **FR-003:** The fix command formats all code and fixes the mistakes that can be fixed safely; every other mistake is listed with its file and line.
- **FR-004:** The check is part of the tests, so it runs locally and for every pull request.
- **FR-005:** All existing code is formatted once, in a commit with only formatting changes, which the file history on GitHub skips.

## Non-Functional Requirements
- **NFR-001:** The check of all files takes at most 5 seconds.

## Boundaries
- None

## Constraints
- It works with TypeScript 7, which Mordoc uses.

## Risks
- Formatting all code conflicts with open pull requests that touch the same files.
- Some mistakes the check finds may need real fixes, not only formatting.

## Open Issues
- None
