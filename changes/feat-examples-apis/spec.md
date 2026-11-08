# APIs example site: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a fresh copy of the repo, when someone follows the site's instructions, then they can build the site and open it in a browser.
- **AC-002:** Given the full list of API features, when someone goes through the site, then they find each one.
- **AC-003:** Given any API page, when it is opened in light and dark theme, then its content is visible and works.
- **AC-004:** Given any API operation, when someone looks in the navigation, then it has a link.
- **AC-005:** Given the finished change, when the Mordoc code is compared with before, then it is identical, and the Mordoc package people install contains Mordoc only.

## Functional Requirements
- **FR-001:** A contributor can run the site from a copy of the repo, using the Mordoc code in that copy, by following short instructions.
- **FR-002:** A visitor can read API pages for two small APIs, showing parameters, requests, responses, data types, deprecated operations and webhooks.
- **FR-003:** A visitor can see examples of each kind: written in the API file, written in a separate file, and generated from the data types.
- **FR-004:** A visitor can read added explanations on an operation and a data type, including labels on fields.
- **FR-005:** A visitor can reach every operation from the navigation, with labels taken from the API file or written by hand.

## Non-Functional Requirements
- **NFR-001:** The site stays small, under 1 MB.
- **NFR-002:** All content is fictional.
- **NFR-003:** Mordoc needs no new dependencies for this site.
- **NFR-004:** Everything on the site can be checked by automated browser tests.

## Boundaries
- None

## Constraints
- None

## Risks
- API features aren't covered in the Mordoc documentation, so correct use has to be worked out from the code.

## Open Issues
- None
