# Mark only the current page in the sidebar after opening an address that ends in a slash: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `samePath` in `src/app/path-utils.ts` ignores a trailing slash and letter case.
  - The sidenav leaf in `src/app/layout/sidenav/Sidenav.tsx` is a `Link` whose active class and `aria-current` come from `samePath`, like the linked group label.
- **FR-002:**
  - `isSameOrBelow(path, base)` in `src/app/path-utils.ts`: `samePath`, or `path` below `base`, ignoring a trailing slash and letter case.
  - `resolveActiveSidenav` in `Sidenav.tsx` and `resolveActiveSidenavRaw` in `src/app/layout/breadcrumb/useBreadcrumb.ts` use `isSameOrBelow` in place of `startsWith`.

## Decisions
- **D-001:** The sidenav leaf compares paths with `samePath` instead of `NavLink` with `end`, because the server renders paths without a slash, and on a hard load of an address with a slash `NavLink`'s exact match differs from the server's, which React doesn't correct when it takes over the page. Rejected: making every address end in a slash, with all links and the address in the browser changed, which changes every page address for a bug in one comparison.
- **D-002:** Paths are compared case-insensitively, because the router matches routes case-insensitively and page slugs are always lowercase, so two pages can never differ only in case. Rejected: case-sensitive comparisons, which leave the sidebar without a current page for a page the router shows.
