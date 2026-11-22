# Browser tests for the components example site: Tasks

**Change:** `test-e2e-components`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-001):** Add `@playwright/test`, the static server `test/e2e/serve.ts`, and `playwright.config.ts`, which builds `examples/components` and serves it before the tests.
- [x] **T-002 (FR-004):** Add the `test:e2e` and `test:build` scripts to `package.json`, each building Mordoc first.
- [x] **T-003 (FR-005):** Let the `test` script run `test:build` and `test:e2e`.
- [x] **T-004 (FR-003):** Add the `light` and `dark` projects to `playwright.config.ts`.
- [x] **T-005 (FR-001):** Add `test/e2e/components.spec.ts` with a test per page that checks each component is visible with its content.
- [x] **T-006 (FR-002):** Add a test per interaction to `test/e2e/components.spec.ts`.
