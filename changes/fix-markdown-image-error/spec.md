# Markdown images cause a browser error: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a built page with a Markdown image or an image tag, on its own line or inside a sentence, when it is opened, then the image shows and the browser logs no errors.
- **AC-002:** Given an image inside a sentence, when the page is opened, then the image shows within the sentence.
- **AC-003:** Given any image, when a reader clicks it, then it opens larger, and pressing Escape closes it.
- **AC-004:** Given any image, when a keyboard user moves to it and presses Enter, then it opens larger.
- **AC-005:** Given an image with a title, when a reader hovers over it, then the title shows.

## Functional Requirements
- **FR-001:** A reader can open any page with images with no browser errors.
- **FR-002:** Every image shows as an image, on its own line and inside a sentence, and opens larger when it is clicked or chosen with the keyboard.
- **FR-003:** An image's title shows when hovering over it.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- None

## Risks
- Images with a title lose their visible caption until the figure tag exists. The Mordoc documentation has none; the components example site has two.

## Open Issues
- None
