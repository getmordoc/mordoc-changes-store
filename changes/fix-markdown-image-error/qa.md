# Markdown images cause a browser error: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Manual checks in Chrome on built sites, served as static files, with Mordoc built from this change's branch. Each site is also built with Mordoc from `main`, to compare.
- Sites: the components example site with extra test pages, which have images and advanced images in every place they can be written and an advanced image inside a sentence; and the Mordoc documentation, in English and German.
- Pages without images must stay exactly the same as with `main`.
- Setup: Node.js 24. In the Mordoc repository `npm install` and `npm run build`; in a site folder `node <mordoc>/bin/cli.js build`, then `python3 -m http.server <port> -d dist`.

## Test Coverage
- **AC-001:** Open pages with a Markdown image and an image tag on their own line, inside a sentence and inside a link, on the components test pages and on the documentation's pages with images. Each is an `<img>`, with no `<figure>` and no empty paragraph, with rounded corners and a shadow, and the browser console has no errors. Compare with the documentation's images page built from `main`, which logs "Minified React error #418".
- **AC-002:** An image inside a sentence is inside that sentence's paragraph.
- **AC-003:** Click an image inside a link: the link's page opens.
- **AC-004:** An image with a title has it as its hover text; an image without one has none.
- **AC-005:** An image tag with its path in a variable shows the image from that path.
- **AC-006:** Open advanced images on their own line, from a variable, without a caption and inside a callout, in light and dark theme: each is a figure with its caption below, rounded corners, a shadow and space above and below, and the console has no errors.
- **AC-007:** An advanced image with its path in a variable shows the image and its caption.
- **AC-008:** Hover over an advanced image: it grows slightly. Hover over an image: nothing changes.
- **AC-009:** Click an advanced image: it opens larger with its caption. Escape, the close button and a click outside the image each close it.
- **AC-010:** Move to an advanced image with the keyboard and press Enter: it opens larger.
- **AC-011:** Read the documentation's image pages and the components example site's images page: they describe images and advanced images, and their style settings, as they work.
