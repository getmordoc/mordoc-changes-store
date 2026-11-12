# Document images and advanced images: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- All changes are in mordoc-docs, under `content/en`, `content/de` and `config/navigation`.
- **FR-001:**
  - `writing-content/advanced-images.md` explains `{% advancedImage src="…" alt="…" caption="…" /%}`, its attributes, opening larger on click or Enter, and that it stands on its own line, with a code block marked `{% process=false %}` and a live example using `/images/content-images/artwork.png`.
- **FR-002:**
  - `customization/advanced/images.md` describes the plain image and lists only `--image-radius` and `--image-shadow`, with an example `image.css`.
  - `customization/advanced/advanced-images.md` lists `--image-radius`, `--image-shadow`, `--image-caption-color`, `--image-overlay-bg` and `--image-close-button-radius`, with an example `image.css`.
  - Both pages say that both kinds of image are styled in `config/styles/image.css` and share radius and shadow.
- **FR-003:**
  - `sidenav.yaml` has an Advanced Images entry right after each Images entry.
  - `translations/de.yaml` has `Advanced Images: Erweiterte Bilder`.

## Decisions
- **D-001:** Advanced images get their own pages, because every other component has its own page. Rejected: a section on the images pages.
