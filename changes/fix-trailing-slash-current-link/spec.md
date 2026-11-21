# Mark only the current page in the sidebar after opening an address that ends in a slash: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a page opened at an address with or without a slash at the end, when the reader opens another page from the sidebar, then only that page is marked as current.
- **AC-002:** Given any page, the address bar shows its address ending in a slash.
- **AC-003:** Given an address without the slash, when the reader opens it, then they see the same page, at the address with the slash.
- **AC-004:** A site's links, sitemap and language switch point to addresses that end in a slash.

## Functional Requirements
- **FR-001:** Every page address ends in a slash; the home page is `/`. Every link to a page that Mordoc shows uses that form: the sidebar, top navigation, breadcrumbs, header links, cards, buttons, links in the content, search results, the language switch, the sitemap and each page's own address for search engines.
  - A link to a file, such as an image or a download, keeps its address without a slash.
  - A link to a heading on a page puts the heading after the slash, as in `/getting-started/run-locally/#install`.
  - An author can keep writing page links without the slash; Mordoc adds it.
- **FR-002:** When a page is opened at an address without the slash, the address in the browser changes to the one with the slash, without loading the page again, before the reader can use the page.
- **FR-003:** The sidebar, top navigation, breadcrumbs and language switch mark the current page the same way, whatever form of the address the reader arrived at.

## Non-Functional Requirements
- **NFR-001:** Correcting the address causes no extra page load and no visible jump.
- **NFR-002:** It works on hosts that add the slash, remove it or accept both.

## Boundaries
- None

## Constraints
- The Mordoc documentation's host must serve page addresses with the slash, so mordoc.dev needs the matching host setting.

## Risks
- Search engines see new addresses for every page once; old addresses keep working because Mordoc corrects them.

## Open Issues
- None
