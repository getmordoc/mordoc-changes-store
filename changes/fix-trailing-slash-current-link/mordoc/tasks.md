# Mark only the current page in the sidebar after opening an address that ends in a slash: Tasks

**Change:** `fix-trailing-slash-current-link`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-001):** Mark the sidenav leaf as current with `samePath`, and let `samePath` ignore letter case.
- [ ] **T-002 (FR-001):** Add the browser test for a page opened with a slash at the end.
- [ ] **T-003 (FR-002):** Find the sidebar section and breadcrumb with `isSameOrBelow`, ignoring a slash and letter case.
- [ ] **T-004 (FR-002):** Add the browser test for an address with capital letters.
