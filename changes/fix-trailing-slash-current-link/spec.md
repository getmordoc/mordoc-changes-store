# Mark only the current page in the sidebar after opening an address that ends in a slash: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The reader sees only the page they are on marked in the sidebar, also after opening an address that ends in a slash.

## Functional Requirements
- **FR-001:** The sidebar marks a page as current when the address is its path, ignoring a slash at the end. The page as it comes from the server and the page once it runs in the browser mark the same page, so no other page stays marked.
  - Screen readers announce only that page as the current page.

## Non-Functional Requirements
- **NFR-001:** It works on hosts that add the slash, remove it or accept both.

## Boundaries
- Page addresses and the links to them stay as they are.

## Constraints
- None

## Risks
- None

## Open Issues
- None
