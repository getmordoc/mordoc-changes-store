# One report for the problems in the content: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The author sees a problem in a page that is also shown in other languages once.
- **AC-002:** The author sees the problems in the pages and in the texts for the API reference, and the error for an OpenAPI file that can't be loaded, in one list.
- **AC-003:** The author sees each problem once in the preview, when it starts and after a page is saved.

## Functional Requirements

### FR-001: One list of problems
Mordoc lists the problems in the pages and in the texts for the API reference together, under one heading, such as "Mordoc found 2 problems in your content:". Each problem is listed once.

- A page that is also shown in other languages, because it has no translation, has its problems listed once, with its own file.
- Each problem is one line with the file and line, the level and the message, such as `content/en/page.md:5  critical  Undefined tag: 'banner'`. A problem without a file has only the level and the message.

### FR-002: The list when another error stops the build
When another error stops the build, such as an OpenAPI file that can't be loaded, Mordoc adds that error to the list, without a file, and stops after the list. With `--verbose`, the error also shows where in Mordoc it happened.

### FR-003: Problems in the preview
The preview lists the problems when it starts. After the author saves a page, it lists the problems of that page, each once.

## Non-Functional Requirements
None

## Boundaries
- None

## Constraints
- It is released in Mordoc 2.2.0, together with the changes for names and paths that follow it.

## Risks
- None

## Open Issues
- None
