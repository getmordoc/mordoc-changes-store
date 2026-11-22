# Browser tests for the components example site: QA Plan

**Change:** `test-e2e-components`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- The change adds tests only; Mordoc's code and the components example site are not changed, and the validation tests must keep passing.
- Setup: `npm ci` on Node 24 and `npx playwright install chromium` once; run the browser tests with `npm run test:e2e`, the validation tests with `npm run test:build`, and all tests with `npm test`.
- Check that the tests are trustworthy by temporarily breaking a component and seeing a test fail.

## Test Coverage
- **AC-001:** `npm run test:e2e` passes in the `light` and the `dark` project; each page test checks that every component on that page is visible with its content. In the `dark` project the page has the dark theme.
- **AC-002:** `npm run test:e2e` passes; each interaction from FR-002 has its own test, which checks the result the reader sees, such as an open accordion, an enlarged image, a playing clip or the copied text.
- **AC-003:** Temporarily break a component in Mordoc, such as the accordion, and run `npm run test:e2e`: at least one test fails and its name and error name the page and the component. Undo the change afterwards.
- **AC-004:** In a fresh clone, `npm ci`, `npx playwright install chromium` and `npm run test:e2e` build Mordoc and the site and run only the browser tests, within two minutes.
- **AC-005:** In a fresh clone, `npm test` runs the validation tests and the browser tests and reports both results.
