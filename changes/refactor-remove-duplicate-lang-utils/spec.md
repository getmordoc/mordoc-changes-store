# Remove the duplicate language helpers: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the finished change, when Mordoc is compiled, then it succeeds with no errors.
- **AC-002:** Given the sites in more than one language, when they are built before and after the change, then they produce the same pages, each with the same language.
- **AC-003:** Given the finished change, when someone looks through the code, then they find the language helpers only once, and the build uses no website code.
- **AC-004:** Given the finished change, when the tests run, then they pass.

## Functional Requirements
- **FR-001:** The build gives each page its language from what it already knows about the page.
- **FR-002:** The language helpers exist once, in the website.

## Non-Functional Requirements
- **NFR-001:** Generated sites stay the same.

## Boundaries
- None

## Constraints
- None

## Risks
- None

## Open Issues
- None
