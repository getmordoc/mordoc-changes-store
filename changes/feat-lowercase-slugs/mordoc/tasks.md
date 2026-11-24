# Lowercase page addresses from file names: Tasks

**Change:** `feat-lowercase-slugs`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [ ] **T-001 (FR-007):** Let `ContentValidator` keep problems that don't come from Markdoc, and report each problem once.
- [ ] **T-002 (FR-001, FR-007, FR-008):** Check the names of pages and their folders, with build tests.
- [ ] **T-003 (FR-001):** Check the author's part of an API page's address, with build tests.
- [ ] **T-004 (FR-002, FR-003):** Make page and API addresses lowercase, with build tests.
- [ ] **T-005 (FR-002):** Make the language in an address lowercase, in the build and the app, with build tests.
- [ ] **T-006 (FR-004, FR-008):** Report duplicate addresses over all languages and API pages, with build tests.
- [ ] **T-007 (FR-006):** Add `createRouteResolver`, with the addresses of the operations known before the pages are transformed.
- [ ] **T-008 (FR-005, FR-006):** Replace and check paths in pages and enrichment files, remove the missing link from the example site, with build tests.
- [ ] **T-009 (FR-005, FR-006):** Replace and check paths in the navigation, header, footer and footer translations, with build tests and the browser test.
- [ ] **T-010 (FR-008, FR-009):** Apply the same rules in the preview after each saved file, with preview tests.
