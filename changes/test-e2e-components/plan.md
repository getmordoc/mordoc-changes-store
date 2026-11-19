# Browser tests for the components example site: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in the `mordoc` repository.
- `test/e2e/` holds the browser tests, one file per example site, next to `test/build/`.
- **FR-001:**
  - `@playwright/test` is a dev dependency, with Chromium as the test browser.
  - `test/e2e/serve.ts` serves a built site's `dist/` as a static host does: each page address gets its own `index.html`, and an unknown address gets a 404.
  - `playwright.config.ts` builds `examples/components` and serves its `dist/` with `test/e2e/serve.ts` before the tests.
  - `test/e2e/components.spec.ts` has a test per page that checks each component is visible with its content.
- **FR-002:**
  - `test/e2e/components.spec.ts` has a test per interaction.
- **FR-003:**
  - `playwright.config.ts` has a `light` and a `dark` project; the `dark` project stores `mordoc-theme: dark` in local storage before each page loads.
- **FR-004:**
  - `package.json` has a `test:e2e` script that runs Playwright, and a `test:build` script that runs the validation tests, each building Mordoc first.
- **FR-005:**
  - `package.json` has a `test` script that runs `test:build` and `test:e2e`.

## Decisions
- **D-001:** Use Playwright, because it runs real browsers, starts the site itself and works on every operating system and in CI. Rejected: Cypress.
- **D-002:** Check what readers see and can do, because screenshots differ per operating system and browser. Rejected: comparing screenshots.
- **D-003:** Test in Chromium only, because it is the fastest and enough to find broken components. Rejected: also Firefox and WebKit.
- **D-004:** Serve the built site with a small Node server, because Mordoc has no preview command and `vite preview` serves the home page for a page address without a trailing slash, as no static host does. Rejected: `vite preview`, and the dev server, which doesn't test the build.
- **D-005:** Set the dark theme through local storage before each page loads, so every test runs once per theme. Rejected: clicking the theme switch in every test.
