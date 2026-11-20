# Make the site usable with a keyboard and a screen reader: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, in `src/app/`, following the WAI-ARIA Authoring Practices patterns.
- **FR-001:**
  - `LanguagePicker.tsx` shows the languages as a list of `<button>` elements, with `aria-current` on the current language.
  - The trigger has `aria-expanded` and `aria-controls`; opening moves focus to the current language, the arrow keys, Home and End move focus between the buttons, Escape closes the list and focuses the trigger, and a `focusin` outside the picker closes it.
- **FR-002:**
  - The search input has `role="combobox"`, `aria-expanded`, `aria-controls` and `aria-activedescendant` pointing to the selected result, and handles the arrow keys, Enter and Escape.
  - The results are `<a>` elements with `role="option"`, `aria-selected` and an `id`, inside an element with `role="listbox"`.
- **FR-003:**
  - `Diagram.tsx` wraps the inline diagram in a `<button type="button">` with `aria-haspopup="dialog"`, styled like the trigger in `AdvancedImage.tsx`.
- **FR-004:**
  - The diagram, image and search previews are native `<dialog>` elements, opened with `showModal()`; the browser moves focus into them, keeps it there, closes them on Escape and returns focus afterwards.
  - A click on the backdrop is caught by a listener on the `<dialog>` element and closes it.
- **FR-005:**
  - `SceneSvg.tsx` renders the diagram with `role="img"` and `aria-label` set to the new UI string `diagram.label`, in all 13 locales.
- **FR-006:**
  - The 15 `biome-ignore lint/a11y` comments are removed.
- **FR-007:**
  - `test/e2e/accessibility.spec.ts` holds the keyboard-only tests, next to `components.spec.ts`, and runs with `npm test`.
- **NFR-001:**
  - The new buttons have the same `:focus-visible` outline as the search bar, and no other visible change.

## Decisions
- **D-001:** The native `<dialog>` element, because the browser then handles focus, Escape and the rest of the page as the platform intends. Rejected: focus handling and Escape listeners written by hand.
- **D-002:** The language list as buttons, because choosing a language navigates to another page, which buttons describe better than a form list. Rejected: a `listbox` with `aria-activedescendant`.
- **D-003:** Search results as links with `role="option"`, because each result opens a page and links are focusable by nature. Rejected: list items with a click handler.
- **D-004:** One translated name, "Diagram", for every diagram, because authors can't name a diagram yet. Rejected: a new attribute for authors, which is a feature of its own.
