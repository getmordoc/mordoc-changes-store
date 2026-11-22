# Make the site usable with a keyboard and a screen reader: Tasks

**Change:** `fix-accessibility`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-004, FR-006):** Make the image, diagram and search previews native `<dialog>` elements, and remove their `biome-ignore` comments.
- [x] **T-002 (FR-003, FR-005, FR-006):** Open a diagram's preview with a button, name each diagram with the new `diagram.label` in all 13 locales, and remove their `biome-ignore` comments.
- [x] **T-003 (FR-002, FR-006):** Make the search field a combobox with the results as options, and remove their `biome-ignore` comments.
- [x] **T-004 (FR-001, FR-006):** Show the languages as buttons with keyboard support, and remove their `biome-ignore` comments.
- [x] **T-005 (FR-007):** Add `test/e2e/accessibility.spec.ts` with the keyboard-only tests for the previews, the diagram's name and search.
