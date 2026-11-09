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
- **AC-001:** Followed the README in the working copy: the site builds with no warnings and opens in the browser, built and in development. (Passed)
- **AC-002:** Compared each page with the tags and attributes in `createDefaultMarkdocConfig()` and the sequence diagram syntax. Every page renders, with no raw Markdoc tags left. Left out until their bugs are fixed: a file download link and a diagram on the landing page. (Passed)
- **AC-003:** Switched between light and dark theme; opened the accordions, played the clip, searched the site, opened the "page not found" screen through a link, and checked the diagram and the footer. The copy button on code blocks is not checked yet. The images page logs a browser error, see [fix-markdown-image-error](../fix-markdown-image-error/proposal.md). (Passed)
- **AC-004:** `npm pack --dry-run` lists no files from `examples/`. (Passed)
- **AC-005:** `git diff main -- src bin package.json` shows no changes. (Passed)
- **NFR-002:** The site's own files are 99 KB. (Passed)
- **NFR-004:** The site's `package.json` has no dependencies, and Mordoc's `package.json` is unchanged. (Passed)
