# Tests for content validation: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the test site with mistakes, when the tests run, then they pass only if the build stops and reports every mistake with the expected file, line, level and message.
- **AC-002:** Given the test site with only warnings, when the tests run, then they pass only if the build finishes and reports exactly the expected warnings.
- **AC-003:** Given the test site with only correct content, when the tests run, then they pass only if the build finishes without reporting anything.
- **AC-004:** Given a change that breaks a validation rule, when the tests run, then at least one test fails and shows the difference between the expected and the reported problems.
- **AC-005:** Given a fresh copy of the repository, when a contributor runs one command, then all validation tests run and report the result.

## Functional Requirements
- **FR-001:** A test site with mistakes covers every kind of error validation reports: an unknown tag, an invalid option value, an undefined variable in text and in a code block, a block tag inside a sentence and inside a link, an advanced image inside a sentence and inside a link, and a link or button inside a link.
- **FR-002:** A test site with only warnings covers the warnings validation reports, such as a Markdown image inside a link.
- **FR-003:** A test site with only correct content covers what validation allows, such as an image tag inside a link, a code block shown as written, and variables in code blocks.
- **FR-004:** The tests build each test site and compare the reported problems and the outcome of the build with what is expected.
- **FR-005:** One command runs all validation tests.

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
