# Mark only the current page in the sidebar after opening an address that ends in a slash: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The reader sees only the page they are on marked in the sidebar, also after opening an address that ends in a slash.
- **AC-002:** The reader sees the sidebar and breadcrumb, with the current page marked, also at an address with capital letters, such as `/Media/Images`.

## Functional Requirements
- **FR-001:** The sidebar marks a page as current when the address is its path, ignoring a slash at the end and letter case. The page as it comes from the server and the page once it runs in the browser mark the same page, so no other page stays marked.
  - Screen readers announce only that page as the current page.
- **FR-002:** The sidebar section and the breadcrumb for an address are found the same way, ignoring a slash at the end and letter case, also for pages below a top navigation item, such as `/Media/Images` below `/media`.

## Non-Functional Requirements
- **NFR-001:** It works on hosts that add the slash, remove it or accept both.

## Boundaries
- Page addresses and the links to them stay as they are.

## Constraints
- None

## Risks
- A host that finds files case-sensitively, as most do, still shows its "page not found" page when an address with capital letters is opened directly; only addresses reached inside the site, or on hosts that ignore case, show the page.

## Open Issues
- None
