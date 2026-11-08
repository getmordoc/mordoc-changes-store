# Links to site files show "page not found": Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a page with a link to a file on the site, when a reader clicks it, then the file opens or downloads.
- **AC-002:** Given a link to another page, when a reader clicks it, then the page opens with no full page reload.
- **AC-003:** Given a link to a page that doesn't exist, when a reader clicks it, then the "page not found" screen shows.

## Functional Requirements
- **FR-001:** A reader can open or download a file from a link in a page.
- **FR-002:** Links to pages work as they do today.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- None

## Risks
- Mordoc has to tell links to files from links to pages, so a page address that looks like a file name could be treated as a file.

## Open Issues
- None
