# Close the mobile menu when the window becomes wide: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the mobile menu is open, when the window becomes wide enough for the sidebar, then the menu closes and the page looks and scrolls as usual.
- **AC-002:** Given a narrow window, a reader can still open and close the mobile menu, and the page behind it does not scroll while it is open.

## Functional Requirements
- **FR-001:** When the window becomes wide enough for the sidebar while the mobile menu is open, the menu closes and the page scrolls again from the place the reader was.
- **FR-002:** Nothing darkens the page when the window is wide.

## Non-Functional Requirements
- **NFR-001:** It works when the window is resized, a tablet is turned, or the browser zoom changes the width.

## Boundaries
- None

## Constraints
- None

## Risks
- None

## Open Issues
- None
