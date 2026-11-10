# Markdown images cause a browser error: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a built page with a Markdown image or an image tag, on its own line, inside a sentence or inside a link, when it is opened, then the image shows with rounded corners and a shadow, and the browser logs no errors.
- **AC-002:** Given an image inside a sentence, when the page is opened, then the image shows within the sentence.
- **AC-003:** Given an image inside a link, when a reader clicks it, then the link opens.
- **AC-004:** Given an image with a title, when a reader hovers over it, then the title shows.
- **AC-005:** Given an image tag with its path in a variable, when the page is opened, then the image from the variable's path shows.
- **AC-006:** Given a figure with a caption, when the page is opened, then the image shows with rounded corners, a shadow, space above and below, and the caption below it, and the browser logs no errors.
- **AC-007:** Given a figure with its path in a variable, when the page is opened, then the image from the variable's path shows.
- **AC-008:** Given a figure, when a reader hovers over it, then it grows slightly.
- **AC-009:** Given a figure, when a reader clicks it, then it opens larger with its caption, and pressing Escape, clicking the close button or clicking outside the image closes it.
- **AC-010:** Given a figure, when a keyboard user moves to it and presses Enter, then it opens larger.
- **AC-011:** Given a figure inside a sentence or a link, when the site is built, then the build reports the file, the line, and that a figure must stand on its own line.
- **AC-012:** Given the Mordoc documentation and the components example site, when a writer reads them, then they describe images and figures, and their style settings, as they work.

## Functional Requirements
- **FR-001:** A reader can open any page with images or figures with no browser errors.
- **FR-002:** An image shows as a plain image, wherever it is written, with rounded corners and a shadow. Its title shows when hovering over it, and an image tag can take its path from a variable.
- **FR-003:** A figure has everything the image tag has today: a caption below the image, rounded corners, a shadow, space above and below, a hover effect, and a path that can come from a variable.
- **FR-004:** A figure opens larger when it is clicked or chosen with the keyboard, and closes with Escape, the close button or a click outside the image.
- **FR-005:** A figure stands on its own line; a figure inside a sentence or a link is reported.
- **FR-006:** The Mordoc documentation and the components example site describe images and figures as they work.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- Reporting a figure that is not on its own line relies on [content validation](../feat-markdoc-validation/proposal.md), so this change is released together with it or after it.

## Risks
- Images with a title lose their visible caption, and have to become figures to keep it. The components example site has two; the Mordoc documentation has none.

## Open Issues
- None
