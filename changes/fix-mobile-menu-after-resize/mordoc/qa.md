# Close the mobile menu when the window becomes wide: QA Plan

**Change:** `fix-mobile-menu-after-resize`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- A browser test on the components example site covers the resize; the existing tests cover the mobile menu on a narrow window.
- Run `npm test`.

## Test Coverage
- **AC-001:** A browser test opens the mobile menu at phone width, widens the window past the breakpoint, and checks that the menu button reports the menu as closed, no backdrop covers the page, and the page scrolls.
- **AC-002:** The same test first checks, at phone width, that the menu opens and that the page behind it does not scroll; the existing tests keep covering closing it.
