# Modernize Mordoc's default look and feel: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** A reader sees each sidebar category below a thin line, with a title that is larger and bolder than the pages in it.
- **AC-002:** A reader sees a thin line above each main heading on a page.
- **AC-003:** A reader sees dark code blocks in light and dark mode, with code that is easy to read.
- **AC-004:** A reader sees the current page in the sidebar in red text, without a colored background.
- **AC-005:** A reader sees calmer text: a smaller page title, a larger intro under it, softer body text and a quieter "On this page" list.
- **AC-006:** A site owner who changes colors or styles with their own style files still sees those changes.

## Functional Requirements
- **FR-001:** A top-level sidebar group without its own page is a category. Its title is in capitals, bolder and larger than before, and in the main text color. From the second item in the sidebar on, a thin line separates each category from what is above it. A category still opens and closes as it does today.
- **FR-002:** Pages in the sidebar are in regular weight. The current page is in the accent color and bold, without a background.
- **FR-003:** Each main heading on a page has a thin line above it, unless it is the first thing on the page.
- **FR-004:** The page title is smaller and the intro under it larger, so they read as one header. Headings are smaller, body text is a softer dark grey, and the "On this page" title is small and in capitals.
- **FR-005:** Code blocks are dark in light and dark mode, including the code examples on API pages and code without a language:
  - the title bar is a little darker than the code;
  - the code is light, with highlight colors that are easy to read on the dark background;
  - in dark mode, a thin border keeps the block apart from the page.
- **FR-006:** The red accent color stays, and every style setting a site owner can change today still works.

## Non-Functional Requirements
- **NFR-001:** All text, including code and its highlight colors, has enough contrast to read: at least 4.5:1.
- **NFR-002:** The new look works in light and dark mode, and on small screens.

## Boundaries
- None

## Constraints
- The font stays Inter.

## Risks
- Sites that change Mordoc's styles with their own files may look different after updating.

## Open Issues
- None
