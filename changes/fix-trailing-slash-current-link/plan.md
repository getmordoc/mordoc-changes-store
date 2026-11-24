# Mark only the current page in the sidebar after opening an address that ends in a slash: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `samePath` in `src/app/path-utils.ts` ignores a trailing slash and letter case.
  - The sidenav leaf in `src/app/layout/sidenav/Sidenav.tsx` is a `Link` whose active class and `aria-current` come from `samePath`, like the linked group label.

## Decisions
- **D-001:** The sidenav leaf compares paths with `samePath` instead of `NavLink` with `end`, because the server renders paths without a slash, and on a hard load of an address with a slash `NavLink`'s exact match differs from the server's, which React doesn't correct when it takes over the page. Rejected: making every address end in a slash, with all links and the address in the browser changed, which changes every page address for a bug in one comparison.
- **D-002:** `samePath` also ignores letter case, because the router matches routes case-insensitively and `NavLink`, which it replaces, did too. Rejected: a case-sensitive `samePath`, which would mark fewer links than `NavLink` did.
