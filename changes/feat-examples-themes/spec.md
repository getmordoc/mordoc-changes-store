# Themes example site: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a fresh copy of the repo, when someone follows the site's instructions, then they can build the site and open it in a browser.
- **AC-002:** Given the site with and without its custom theme and branding, when the same page is compared, then the colors, fonts and logo visibly differ in light and dark theme.
- **AC-003:** Given a built page, when its source is read, then it contains the site's custom head content, metadata and browser tab icon.
- **AC-004:** Given the built site, when someone clicks a link in the side navigation, then the page opens.
- **AC-005:** Given the finished change, when the Mordoc code is compared with before, then it is identical, and the Mordoc package people install contains Mordoc only.

## Functional Requirements
- **FR-001:** A contributor can run the site from a copy of the repo, using the Mordoc code in that copy, by following short instructions.
- **FR-002:** A visitor sees the site in its own colors, in light and dark theme, with one component in its own custom style.
- **FR-003:** A visitor sees the site's own fonts for text and code, its logos for light and dark theme, and its browser tab icon. Each page has custom head content and metadata.
- **FR-004:** A visitor can use side navigation with nested groups and open groups, and can read a landing page and a few article pages with enough components to show the theme.
- **FR-005:** The site has one language and content pages only.

## Non-Functional Requirements
- **NFR-001:** The site stays small, under 1 MB including fonts.
- **NFR-002:** All content is fictional, images are made for this site, and fonts have a license that allows sharing them, included with the site.
- **NFR-003:** Everything on the site can be checked by automated browser tests.

## Boundaries
- None

## Constraints
- None

## Risks
- Building the site may turn up bugs. Each one is reported, and the affected feature is added once it's fixed.

## Open Issues
- None
