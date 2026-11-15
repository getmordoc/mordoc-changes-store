# Document images and advanced images: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Build mordoc-docs with local Mordoc `main` (`node ../mordoc/bin/cli.js build`) and check the pages in Chrome, in English and German.
- Read each token on the styling pages against the image and advanced image styles in Mordoc.

## Test Coverage
- **AC-001:** Open Advanced Images under Writing Content: the text covers caption, click or Enter to enlarge and own line; the live example shows the caption and opens larger on click and on Enter; the code block shows the tag as written.
- **AC-002:** Open Images under Customization: it lists only `--image-radius` and `--image-shadow`, and both are used by the plain image in Mordoc.
- **AC-003:** Open Advanced Images under Customization: its five tokens are exactly the ones the advanced image uses in Mordoc.
- **AC-004:** In the side navigation, Advanced Images comes right after Images in both places, and both links open.
- **AC-005:** Repeat AC-001 to AC-004 on the German pages; the navigation shows Erweiterte Bilder.
- **AC-006:** The build finishes, reports no problems, and Chrome shows no console errors on the four pages.
- **AC-007:** Open Images under Writing Content, in English and German: the image tag section lists `src`, `alt` and `title`, which are exactly the image tag's attributes in Mordoc; the live example renders the image with its title on hover; the code block shows the tag as written.
