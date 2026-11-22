# Make the site usable with a keyboard and a screen reader: QA Plan

**Change:** `fix-accessibility`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Browser tests in `test/e2e/accessibility.spec.ts` use the keyboard only, on the built `examples/components` site, in the light and dark theme.
- The previews are also opened in the dev server, where React's StrictMode runs every effect twice.
- The language picker only shows on a site with more than one language, so it is checked on `../mordoc-docs` (English and German), built with this branch.
- Before the first task, take screenshots of the home, diagrams, images and a guide page on `main`; mouse users must see the same pages afterwards.
- Chrome's accessibility tree for the names and roles screen readers get.
- After each task: `npm test`.

## Test Coverage
- **AC-001:** On `../mordoc-docs`, Tab reaches the picker, Enter opens it with focus on the current language, the arrow keys, Home and End move between the languages, Enter on Deutsch opens the German page, and Escape or moving focus out of the list closes it; the picker has `aria-expanded`, and the current language `aria-current`.
- **AC-002:** A browser test types a search, presses the down arrow, and checks that the search field's `aria-activedescendant` names the selected result and that only that result is selected.
- **AC-003:** A browser test reaches a diagram with Tab, opens its preview with Enter, checks that focus is inside the preview and stays there with Tab, uses the zoom buttons, closes the preview with Escape and with its close button, and checks each time that focus is back on the diagram; the same for the image preview and the search window. In the dev server, each preview stays open. Selecting text in the search field and releasing on the backdrop keeps it open.
- **AC-004:** A browser test finds each diagram named "Diagram", and Chrome's accessibility tree shows its labels readable; on the German pages of `../mordoc-docs` the name is German.
- **AC-005:** No `biome-ignore lint/a11y` is left in the code, and `npm run check` passes.
- **AC-006:** `npm test` runs `test/e2e/accessibility.spec.ts`, and its tests pass locally and in the pull request's `test` check.
- **NFR-001:** The screenshots match the ones taken on `main`, apart from the focus outline when the keyboard is used.
