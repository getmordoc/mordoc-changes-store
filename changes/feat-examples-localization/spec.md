# Localization example site: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a fresh copy of the repo, when someone follows the site's instructions, then they can build the site and open it in a browser.
- **AC-002:** Given a translated page, when a visitor switches to German, then the same page opens in German, with translated navigation and footer.
- **AC-003:** Given the page that exists only in English, when a visitor opens its German address, then they see the English content, and the page is left out of the site's page list for search engines.
- **AC-004:** Given an API page, when a visitor opens its German address, then the site around it is German and the API content is English.
- **AC-005:** Given the finished change, when the Mordoc code is compared with before, then it is identical, and the Mordoc package people install contains Mordoc only.

## Functional Requirements
- **FR-001:** A contributor can run the site from a copy of the repo, using the Mordoc code in that copy, by following short instructions.
- **FR-002:** A visitor can read a landing page and a few article pages in English and German, and links between pages stay in the visitor's language.
- **FR-003:** A visitor sees the navigation and footer labels in the selected language.
- **FR-004:** A visitor who opens a page that exists only in English sees the English version.
- **FR-005:** A visitor can open a small API page, with one operation, in both languages.

## Non-Functional Requirements
- **NFR-001:** The site stays small, under 1 MB.
- **NFR-002:** All content is fictional.
- **NFR-003:** Everything on the site can be checked by automated browser tests.

## Boundaries
- None

## Constraints
- None

## Risks
- Building the site may turn up bugs. Each one is reported, and the affected feature is added once it's fixed.

## Open Issues
- None
