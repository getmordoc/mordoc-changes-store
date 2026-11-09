# Broken addresses show the host's error page: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `mordoc build` writes `dist/404.html`, rendered by the SSG runner through the existing SSR entry and route table, from the catch-all `*` route in the default language.
  - `NotFound` shows the opened address only after hydration.
- **FR-002:**
  - `dist/404.html` has the title from `notFound.title` and `<meta name="robots" content="noindex">`.
  - The Pagefind index has no entry for `dist/404.html`.
  - `sitemap.xml` has no entry for it.
- **FR-003:**
  - None

## Decisions
- **D-001:** Show the opened address only after hydration, because the same `404.html` is served at every unknown address, so an address in the static HTML would not match the browser's address and break hydration. Rejected: leaving the address out.
- **D-002:** Render `404.html` through the existing SSR entry and route table, because the page then looks and works like the existing "page not found" page. Rejected: a separate HTML template.
