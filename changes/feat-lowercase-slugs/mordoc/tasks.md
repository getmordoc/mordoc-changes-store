# Lowercase page paths from file names: Tasks

**Change:** `feat-lowercase-slugs`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-007):** Collect the problems of Markdoc and of Mordoc in `BuildReport`, and report each problem once.
- [x] **T-002 (FR-001, FR-007, FR-008):** Check the names of pages and their folders, with build tests.
- [x] **T-003 (FR-001):** Check the author's part of an API page's path, with build tests.
- [x] **T-004 (FR-002, FR-003):** Make page and API paths lowercase, with build tests.
- [x] **T-005 (FR-002):** Make the language in a path lowercase, in the build and the app, with build tests.
- [x] **T-006 (FR-004, FR-008):** Report pages with the same `routePath` over all languages and API pages, with build tests.
- [ ] **T-007 (FR-004, FR-006):** Report folders in `public` that differ from a page's path only in letter case, and let `RouteMap` find the page of a path, with the `routePath`s of the operations known before the pages are transformed.
- [ ] **T-008 (FR-005, FR-006):** Replace and check paths in pages and enrichment files, remove the missing link from the example site, with build tests.
- [ ] **T-009 (FR-005, FR-006):** Replace and check paths in the navigation, header, footer and footer translations, with build tests and the browser test.
- [ ] **T-010 (FR-008, FR-009):** Apply the same rules in the preview after each saved file, with preview tests.
