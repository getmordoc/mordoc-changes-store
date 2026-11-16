# Tests for content validation: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the test site with mistakes, when the tests run, then they pass only if the build stops and reports every critical problem, error and warning with the expected file, line, level and message.
- **AC-002:** Given a change that breaks a validation rule, when the tests run, then at least one test fails and shows the difference between the expected and the reported problems.
- **AC-003:** Given a fresh copy of the repository, when a contributor runs one command, then all validation tests run and report the result.

## Functional Requirements
- **FR-001:** A test site with mistakes covers every kind of problem validation reports:
  - Errors and critical problems: an unknown tag, an invalid option value, an undefined variable in text and in a code block, a block tag inside a sentence and inside a link, an advanced image inside a sentence and inside a link, a link or button inside a link, a hero or section on an article page, and a mistake in an API description file.
  - Warnings: a Markdown image inside a link, and text inside a callout that stands in a sentence or a link.
- **FR-002:** The tests build the test site and compare the reported problems and the outcome of the build with what is expected.
- **FR-003:** One command runs all validation tests.

## Non-Functional Requirements
- **NFR-001:** The validation tests run in seconds and need no browser.
- **NFR-002:** The tests add no new dependencies to Mordoc.

## Boundaries
- None

## Constraints
- [Content validation](../feat-markdoc-validation/proposal.md) is built before these tests.

## Risks
- None

## Open Issues
- None
