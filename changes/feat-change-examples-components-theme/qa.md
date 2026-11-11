# Journey theme for the components example site: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Build the site from this change's branch and open every page in Chrome, in light and dark theme. Compare each page's tags and attributes with the site on `main`.
- Mordoc's own code must stay unchanged.
- Setup: Node.js 24. In the repository root `npm run build`; in `examples/components` `npm run build` and `python3 -m http.server 4173 -d dist`.

## Test Coverage
- **AC-001:** Search the site's source and the built site for Orbit, space, planets and stars, in texts, file names, image contents and alt texts: none are left. Watch the video and the diagram.
- **AC-002:** Open the site: the browser tab, header, footer and home page show the journey theme.
- **AC-003:** For each page, list its tags and their attributes in the source on `main` and on this branch: the lists are the same, except for attribute values such as texts and paths, and the image inside a link on the images page, which is now an image tag.
- **AC-004:** Open the images, advanced images and video pages: the images, captions and video show the journey theme, and the clip plays.
- **AC-005:** Build the site: no validation problems. Open every page in light and dark theme: the browser console has no errors.
- **AC-006:** Open the home page in light and dark theme: the hero has a light grey background in light mode and a dark grey one in dark mode, and its title and text are readable.
- **NFR-001:** Search the site for names from existing stories: none are used.
- **NFR-002:** The site's own files are under 1 MB.
