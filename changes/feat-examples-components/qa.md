# Components example site: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Manual checks in Chrome, on the built site and in the development server. The automated checks come with the [browser tests for this site](../test-e2e-components/proposal.md).
- Mordoc's own code must stay unchanged.
- Setup: Node.js 24.18.1 or later. In the repository root `npm install` and `npm run build`, then in `examples/components`:
  - `npm run build` and `python3 -m http.server 4173 -d dist`, then open http://localhost:4173
  - `npm run dev` for the development server

## Test Coverage
- **AC-001:** Follow the README in a fresh copy of the repository: the site builds with no warnings and opens in the browser, built and in the development server.
- **AC-002:** Compare each page with the tags and attributes in `createDefaultMarkdocConfig()` and the sequence diagram syntax: every component and variation is on a page, every page renders, and no raw Markdoc tags are left.
- **AC-003:** Open every page in light and dark theme: its feature is visible and works, and the browser console has no errors. This includes opening the accordions, playing the clip, searching the site, opening the "page not found" screen through a link, the copy button on code blocks, images on their own line, inside a sentence and inside a link, opening an advanced image larger and closing it, the diagram and the footer.
- **AC-004:** `npm pack --dry-run` lists no files from `examples/`.
- **AC-005:** `git diff main -- src bin package.json` shows no changes.
- **NFR-002:** The site's own files are under 1 MB.
- **NFR-004:** The site's `package.json` has no dependencies, and Mordoc's `package.json` is unchanged.
