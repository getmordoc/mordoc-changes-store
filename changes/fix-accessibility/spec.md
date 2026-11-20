# Make the site usable with a keyboard and a screen reader: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** A keyboard user can choose a language in the language picker.
- **AC-002:** A screen reader user hears which search result is selected.
- **AC-003:** A keyboard user can open a diagram's preview, use its buttons and close it.
- **AC-004:** A screen reader user hears a name for each diagram.
- **AC-005:** A contributor's code check covers accessibility in all code, without exceptions.
- **AC-006:** A contributor's tests check what keyboard and screen reader users can do on the components example site.

## Functional Requirements
- **FR-001:** The language picker opens with Enter, Space or the down arrow. The arrow keys move through the languages and Enter chooses one. Escape closes the list and puts the keyboard back on the picker; moving the keyboard out of the list closes it too.
- **FR-002:** The search field tells screen readers that it has a list of results, and which result is selected while the arrow keys move through them.
- **FR-003:** A diagram on a page can be reached with Tab and opens its preview with Enter or Space, like an image already does.
- **FR-004:** When a diagram or image preview opens, the keyboard moves to it and stays inside it until it closes. Escape and the close button close it, and the keyboard is then back where it was.
- **FR-005:** Each diagram has a name that screen readers read, in the reader's language.
- **FR-006:** The code check applies every accessibility rule to all code.
- **FR-007:** Accessibility tests, apart from the components' own tests, use only the keyboard on the components example site: the previews open, keep the keyboard and close, each diagram has a name, and search tells which result is selected.

## Non-Functional Requirements
- **NFR-001:** The site looks the same for mouse users; keyboard users see where the keyboard is.
- **NFR-002:** All of it works with the keyboard alone.

## Boundaries
- None

## Constraints
- None

## Risks
- The browser tests that use the header, search or previews may need updates for the new markup.

## Open Issues
- None
