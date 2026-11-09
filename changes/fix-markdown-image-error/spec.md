# Markdown images cause a browser error: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a built page with a Markdown image or an image tag on its own line, when it is opened, then the image shows in its frame, its title shows below it, and the browser logs no errors.
- **AC-002:** Given that image, when a reader clicks it, then it opens larger, and pressing Escape closes it.
- **AC-003:** Given a built page with a Markdown image or an image tag inside a sentence, when it is opened, then the image shows within the sentence, and the browser logs no errors.
- **AC-004:** Given that image, when a reader clicks it, then it opens larger.

## Functional Requirements
- **FR-001:** A reader can open any page with images with no browser errors.
- **FR-002:** An image on its own line looks and behaves as it does today: in a frame, with its title below it, and it opens larger when clicked.
- **FR-003:** An image inside a sentence shows within the sentence, without a frame or title below it, and opens larger when clicked.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- None

## Risks
- Sites with images inside sentences will look different: today these images break the sentence and show in a frame.

## Open Issues
- None
