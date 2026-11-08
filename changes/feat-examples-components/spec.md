# Components example site: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a fresh copy of the repo, when someone follows the site's instructions, then they can build the site and open it in a browser.
- **AC-002:** Given the full list of Mordoc components, when someone goes through the site, then they find each component in every variation it offers.
- **AC-003:** Given any page, when it is opened in light and dark theme, then its feature is visible and works.
- **AC-004:** Given someone installs Mordoc, when they look at what they received, then it contains Mordoc only.
- **AC-005:** Given the finished change, when the Mordoc code is compared with before, then it is identical.

## Functional Requirements
- **FR-001:** A contributor can run the site from a copy of the repo, using the Mordoc code in that copy, by following short instructions.
- **FR-002:** A visitor can see every component in each of its variations, including tables and sequence diagrams.
- **FR-003:** A visitor can open a landing page, read article pages with a table of contents, reach the "page not found" screen, and see images and files that belong to the site.
- **FR-004:** A visitor can move around the site using top navigation with at least two areas, header links and a footer. The site has one language and the default look.

## Non-Functional Requirements
- **NFR-001:** Each page is short and focused on one feature.
- **NFR-002:** The site stays small, under 1 MB.
- **NFR-003:** All content is fictional, images are made for this site, and it can be built offline.
- **NFR-004:** Mordoc needs no new dependencies for this site.
- **NFR-005:** Everything on the site can be checked by automated browser tests.

## Boundaries
- None

## Constraints
- None

## Risks
- Building the site may turn up bugs. Each one is reported, and the affected feature is added once it's fixed.

## Open Issues
- None
