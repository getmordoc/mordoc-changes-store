# Mark only the current page in the sidebar after opening an address that ends in a slash: QA Plan

**Change:** `fix-trailing-slash-current-link`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Browser tests in `test/e2e/components.spec.ts`, on the built components example site served as static files, in light and dark; the existing tests keep passing.
- `npm run check` and `npm test`.

## Test Coverage
- **AC-001:** Open `/guide/callouts/` with a slash, then another page from the sidebar: exactly one sidebar link has `aria-current="page"` and the active style, and it is the page opened; the same without the slash; the browser console shows no hydration warning. This test fails without the fix, following the steps to reproduce.
