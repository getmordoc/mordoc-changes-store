# Markdown images cause a browser error: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `Image` renders a `<button type="button">` holding the `<img>`, with no `<figure>` or `<figcaption>`.
- **FR-002:**
  - The button opens the existing lightbox.
  - `Image.module.css` styles the button as an inline element, and the image with its current rounded corners and shadow.
- **FR-003:**
  - The `<img>` has the title as its `title` attribute.

## Decisions
- **D-001:** Render every image as an image without a figure, because HTML allows an image inside a paragraph, and the same syntax then always gives the same result. Rejected: rendering a figure only when the image is alone in a paragraph.
- **D-002:** Open the image with a button, because a button is allowed inside a paragraph and works with the keyboard. Rejected: a click handler on the image.
- **D-003:** Leave the visible caption to the [figure tag](../feat-figure-tag/proposal.md), because a caption needs a figure. Rejected: keeping the caption in this fix.
