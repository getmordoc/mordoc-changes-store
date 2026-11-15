# Mark the Mordoc documentation's Markdoc examples: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the Mordoc documentation, when it is built with Mordoc's content validation, then the build finishes and reports no problems.
- **AC-002:** Given a page with a code block that shows Markdoc syntax, when a reader opens it, then the code block shows exactly what was written, in English and in German.
- **AC-003:** Given the current Mordoc release, when the documentation is built, then every page is the same as before the change.

## Functional Requirements
- **FR-001:** Every code block in the documentation that shows Markdoc syntax is shown exactly as written, in every language.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- The next Mordoc release with content validation is published only after this change is merged.

## Risks
- A new code block with Markdoc syntax needs the same mark; the validation reports it when it is missing.

## Open Issues
- None
