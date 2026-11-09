# Broken addresses show the host's error page: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given a built site on a host that supports a "page not found" page, when a reader opens an address that doesn't exist, then they see the site's "page not found" page, with the site's header and footer and the address they opened.
- **AC-002:** Given that page, when it is opened, then the browser logs no errors.
- **AC-003:** Given that page, when a reader clicks the button to go home, then the home page opens.
- **AC-004:** Given the site's search, when a reader searches for "page not found", then the "page not found" page is not in the results.
- **AC-005:** Given a link to a page that doesn't exist, when a reader clicks it, then the "page not found" page shows, as it does today.

## Functional Requirements
- **FR-001:** A reader who opens an address that doesn't exist sees the site's "page not found" page.
- **FR-002:** The "page not found" page is not in the site's search, its list of pages for search engines, or search engine results.
- **FR-003:** Clicking a broken link inside the site works as it does today.

## Non-Functional Requirements
- None

## Boundaries
- None

## Constraints
- It works on hosts that show a site's own "page not found" page without extra settings, such as Vercel, Netlify, GitHub Pages and Cloudflare Pages.
- There is one "page not found" page, in the site's default language, because these hosts show one page for every address.

## Risks
- A site on its own server, such as nginx or Apache, needs a setting before the page is shown.

## Open Issues
- None
