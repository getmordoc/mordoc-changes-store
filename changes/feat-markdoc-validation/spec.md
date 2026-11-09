# Validate Markdoc content: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a page with an unknown tag, an invalid option value or an undefined variable, when the site is built, then the build stops and reports the file, the line and the problem.
- **AC-002:** Given pages with only warnings, such as wrongly nested content, when the site is built, then the build finishes and reports each warning with the file and the line.
- **AC-003:** Given the development server is running, when an author saves a page with a mistake, then the mistake is reported and the server keeps running.
- **AC-004:** Given a code block with a variable, when the page is opened, then the code block shows the variable's value.
- **AC-005:** Given a code block marked to be shown as written, when the page is opened, then it shows exactly what was written, and its content is not checked.
- **AC-006:** Given a code block with a mistake, such as an undefined variable, when the site is built, then the build stops and reports it.
- **AC-007:** Given the components example site, when it is built, then no problems are reported.

## Functional Requirements
- **FR-001:** Mordoc validates all Markdoc content in every page, including its code blocks, against Markdoc's rules and Mordoc's tags.
- **FR-002:** Each problem is reported with the file, the line, how serious it is and what is wrong.
- **FR-003:** Errors stop the build; warnings are reported and the build finishes.
- **FR-004:** The development server reports problems and keeps running.
- **FR-005:** Variables in code blocks are filled in, unless the code block is marked to be shown as written.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- Mordoc follows Markdoc's own checks and its handling of code blocks.

## Risks
- The Mordoc documentation stops building until its code blocks that show Markdoc syntax are marked to be shown as written, so both are released together.
- Sites with code blocks that look like Markdoc, such as Jinja or Liquid templates, have to mark them to be shown as written.
- Existing sites with mistakes stop building after updating Mordoc.

## Open Issues
- What a tag inside a code block shows, when the code block is not marked to be shown as written.
- Whether markdown in API descriptions is checked in this change.
