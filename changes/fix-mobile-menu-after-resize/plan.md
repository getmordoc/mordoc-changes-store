# Close the mobile menu when the window becomes wide: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `App.tsx` closes the mobile menu when the media query `(max-width: 767.98px)`, the breakpoint in `App.module.css`, stops matching.
  - The existing scroll lock releases the page and restores its scroll position when the menu closes.
- **FR-002:**
  - The `.overlay` element in `App.tsx` and its rules in `App.module.css` are removed.
- A browser test opens the mobile menu at phone width, widens the window, and checks that the menu is closed and the page scrolls.

## Decisions
- **D-001:** Close the menu from a media query listener, because only the app can reset the open state and release the scroll lock. Rejected: hiding the backdrop with CSS on wide windows, which leaves the page locked.
- **D-002:** Remove the backdrop, because it is never visible as intended: below the breakpoint the menu covers the full width, and above it there is no mobile menu. Rejected: keeping it hidden.
