# Validate Markdoc content: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a page with an unknown tag, an invalid option value or an undefined variable, when the site is built, then the build stops and reports the file, the line and the problem.
- **AC-002:** Given pages with only warnings, such as wrongly nested content, when the site is built, then the build finishes and reports each warning with the file and the line.
- **AC-003:** Given the development server is running, when an author saves a page with a mistake, then the mistake is reported and the server keeps running.
- **AC-004:** Given a code block with a variable that the site defines, when the page is opened, then the code block shows the variable's value instead of the variable, and its copy button copies the code with the value.
- **AC-005:** Given a code block marked to be shown as written, when the page is opened, then it shows exactly what was written, and its content is not checked.
- **AC-006:** Given a code block with a mistake, such as an undefined variable, when the site is built, then the build stops and reports it.
- **AC-007:** Given the components example site, when it is built, then no problems are reported.
- **AC-008:** Given the components example site, when a reader opens its code page, then it shows a JavaScript and a shell code block with values from the site's variables, and a code block with Markdoc syntax shown as written.
- **AC-009:** Given an image tag inside a link, when the site is built, then no problem is reported, and clicking the image opens the link.
- **AC-010:** Given a Markdown image inside a link, when the site is built, then the build finishes and reports a warning with the file and the line.
- **AC-011:** Given an advanced image inside a sentence or a link, when the site is built, then the build stops and reports the file, the line, and that the tag should be a block.
- **AC-012:** Given a code block with a tag that shows a component, such as a callout, and not marked to be shown as written, when the page is opened, then the code block shows exactly what was written, and the browser logs no errors.
- **AC-013:** Given a block tag, such as a callout, card or video, inside a sentence or a link, when the site is built, then the build stops and reports the file, the line and the problem.
- **AC-014:** Given a link or a button inside a link or a button, when the site is built, then the build stops and reports that one click can only go to one place.
- **AC-015:** Given every tag in every place it can be written (on its own line, inside a sentence, inside a link, inside a button, and inside each block tag), when the pages are built and opened, then every page that validation lets through shows no browser errors, and every page that shows a browser error is stopped by validation.
- **AC-016:** Given an enrichment file of the API reference with a mistake, such as an unknown tag, when the site is built, then the build stops and reports the file, the line and the problem.
- **AC-017:** Given a hero or a section on a page that is not a landing page, when the site is built, then the build stops and reports the file, the line, and that the tag is not defined there.
- **AC-018:** Given a hero or a section in an enrichment file of the API reference, when the site is built, then the build stops and reports the file, the line, and that the tag is not defined there.

## Functional Requirements
- **FR-001:** Mordoc validates all Markdoc written for the site, in its pages and in the texts for the API reference, including code blocks, against Markdoc's rules and Mordoc's tags.
- **FR-002:** Each problem is reported with the file, the line, how serious it is and what is wrong.
- **FR-003:** Errors stop the build; warnings are reported and the build finishes.
- **FR-004:** The development server reports problems and keeps running.
- **FR-005:** Variables and tags in code blocks are processed as Markdoc processes them, with variables filled in with their value from the site's settings, unless the code block is marked to be shown as written. A code block with a tag that shows a component is shown as written, until Mordoc can show components inside code blocks.
- **FR-006:** The components example site shows code blocks with variables, and a code block shown as written.
- **FR-007:** A tag, such as the image tag, may be placed inside a link, as in Markdoc.
- **FR-008:** An advanced image that is not on its own line stops the build.
- **FR-009:** Every tag states where it may stand; a block tag inside a sentence or a link stops the build.
- **FR-010:** A link or a button inside a link or a button stops the build.
- **FR-011:** An option only accepts the values its component supports.
- **FR-012:** A hero or a section outside a landing page stops the build.

## Non-Functional Requirements
- **NFR-001:** A page with no validation errors shows no browser errors and renders as written, so translated pages can be checked automatically.

## Boundaries
- None

## Constraints
- Mordoc follows Markdoc's own checks and its handling of code blocks.
- Where Mordoc replaces one of Markdoc's own building blocks, such as links or code blocks, it allows exactly what Markdoc allows: no more and no less.

## Risks
- The Mordoc documentation stops building until its code blocks that show Markdoc syntax are marked to be shown as written, so both are released together.
- Sites with code blocks that look like Markdoc, such as Jinja or Liquid templates, have to mark them to be shown as written.
- Existing sites with mistakes stop building after updating Mordoc.
- Variable values appear in the built pages, so a variable must only hold public values, never secrets such as real API keys.

## Open Issues
- None
