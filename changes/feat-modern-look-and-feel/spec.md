# Modernize Mordoc's default look and feel: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** A reader sees each sidebar category below a thin line, with a title that is larger and bolder than the pages in it.
- **AC-002:** A reader sees a thin line above each main heading on a page.
- **AC-003:** A reader sees code blocks with a darker grey title bar, light in light mode and dark in dark mode, with code that is easy to read.
- **AC-004:** A reader sees the current page in the sidebar in red text, without a colored background.
- **AC-005:** A reader sees calmer text: a smaller page title, a larger intro under it, softer body text and a quieter "On this page" list.
- **AC-006:** A site owner who changes colors or styles with their own style files still sees those changes.
- **AC-007:** A reader sees a light grey header on every page and a slightly darker hero banner on landing pages.
- **AC-008:** A reader sees grey bars with a lighter band moving across while a page loads.
- **AC-009:** A reader sees code in a proper code font on Linux, macOS and Windows, in every browser.

## Functional Requirements
- **FR-001:** Each top-level sidebar group is a category. Its title is in capitals, bolder and larger than before, and in the main text color. From the second item in the sidebar on, a thin line separates each category from what is above it. A category still opens and closes as it does today, and a category with its own page still opens that page. A top-level page next to categories lines up with the pages inside them.
- **FR-002:** Pages in the sidebar are in regular weight. The current page is in the accent color and bold, without a background.
- **FR-003:** Each main heading on a page has a thin line above it, unless it is the first thing on the page.
- **FR-004:** The page title is smaller and the intro under it larger, so they read as one header. Headings are smaller, body text is a softer dark grey, and the "On this page" title is small and in capitals.
- **FR-005:** Code blocks, including the code examples on API pages and code without a language, have a title bar in a darker grey than the code:
  - in light mode the code is on a light background, and in dark mode on a dark one;
  - the highlight colors are easy to read on the background of each mode;
  - a thin border keeps the block apart from the page.
- **FR-006:** The red accent color stays, and every style setting a site owner can change today still works. The new colors and font weights are settings too: the code highlight colors, the category title color and weight, and the color of the line above headings, which can also hide it.
- **FR-007:** The header has a light grey background and the hero banner a slightly darker one, in light and dark mode, each with its own setting. The search field in the header has the page color, white or near-black, so it stands out on the header in both modes.
- **FR-008:** While a page loads, its placeholder shows grey bars with a lighter band moving from left to right, in light and dark mode, with settings for both colors.
- **FR-009:** Code, in code blocks and inline, uses the code font that comes with the reader's system, never a typewriter font. Mordoc ships no code font of its own. Code blocks use a compact size, like Stripe.

## Non-Functional Requirements
- **NFR-001:** All text, including code and its highlight colors, has enough contrast to read: at least 4.5:1.
- **NFR-002:** The new look works in light and dark mode, and on small screens.
- **NFR-003:** Each color that is within a barely visible difference of a Material Design color uses that exact Material Design value.

## Boundaries
- None

## Constraints
- The text font stays Inter.

## Risks
- Sites that change Mordoc's styles with their own files may look different after updating.
- Sites that set no header or hero color get a grey header and hero after updating.

## Open Issues
- None
