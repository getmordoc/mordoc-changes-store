# Markdown images cause a browser error: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `markdoc-config.ts` has a `paragraph` node that renders a paragraph holding only one image as that image, without the `<p>`.
  - `Image` has an `inline` prop.
  - The `image` node renders `Image` with `inline`, except in a paragraph that holds only that image.
  - The `image` tag renders `Image` with `inline` when the Markdoc node is inline.
- **FR-002:**
  - `Image` without `inline` renders `<figure>` with `<img>` and `<figcaption>`, and the lightbox, as today.
- **FR-003:**
  - `Image` with `inline` renders a clickable `<img>` with the title as its `title` attribute, and the same lightbox.

## Decisions
- **D-001:** Leave out the paragraph around an image on its own line, because the image keeps its `<figure>` and `<figcaption>`, which is valid HTML and tells screen readers it is a figure with a caption. Rejected: rendering the figure as `<span>` elements inside the paragraph.
- **D-002:** Render an image inside a sentence as a plain `<img>`, because HTML allows no figure inside a paragraph. Rejected: splitting the sentence around a figure.
