# Markdown images cause a browser error: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `Image` renders only an `<img>`, with no `<figure>`, `<figcaption>` or lightbox.
- **FR-002:**
  - `Image.module.css` styles the image with its current rounded corners and shadow.
  - The `<img>` has the title as its `title` attribute.
- **FR-003:**
  - `AdvImage`, made from the previous `Image` component, renders `<figure>` with `<img>` and `<figcaption>`.
  - `AdvImage.module.css`, made from the previous `Image.module.css`, keeps its spacing, rounded corners, shadow, hover effect and `--image-*` token names.
  - `markdoc-config.ts` has an `advImage` tag with `src` (required), `alt` and `caption`, rendered by `AdvImage`.
  - `AdvImage` is registered in `component-map.ts` and in `LandingPage.tsx`'s components map.
- **FR-004:**
  - The image sits in a `<button type="button">` that opens the previous lightbox.
- **FR-005:**
  - The `advImage` tag has `inline: false`.
- **FR-006:**
  - mordoc-docs `customization/advanced/images.md`, in English and German, describes the style settings of the advanced image.
  - mordoc-docs `writing-content/images.md`, in English and German, has a section "Advanced Image", with caption and zoom support.
  - The components example site's `media/images.md` describes images and advanced images, and its image tag with a title becomes an advanced image.

## Decisions
- **D-001:** Render every image as a plain image, because HTML allows an image inside a paragraph and inside a link, and the same syntax then always gives the same result. Rejected: rendering a figure only when the image is alone in a paragraph.
- **D-002:** Offer zoom only on an advanced image, because an advanced image always stands on its own line, so a button is valid there and works with the keyboard. Rejected: zoom on images, which conflicts with links and does not work with the keyboard.
- **D-003:** Every advanced image opens larger when clicked, because the image tag does that today and the advanced image takes over all its functionality. Rejected: a `zoom` option.
- **D-004:** Build `AdvImage` from the previous `Image` component and keep its token names, because existing style overrides and the documented settings keep working. Rejected: a new component.
- **D-005:** Name the visible text `caption`, because `title` shows when hovering. Rejected: `title`.
- **D-006:** Name the tag `advImage`, called "Advanced Image" in the documentation, because a figure is not zoomable by default in HTML or in other documentation tools. Rejected: `figure`.
