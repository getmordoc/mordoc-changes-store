# Tests for content validation: QA Plan

**Change:** `test-markdoc-validation`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- The change adds tests only; Mordoc's code is not changed.
- NFR-002: `package.json` has no new dependencies after the change.
- Setup: `npm ci` on Node 24; run the tests with `npm test`, which builds Mordoc first.
- Check that the tests are trustworthy by temporarily breaking a validation rule and seeing a test fail.

## Test Coverage
- **AC-001:** `npm test` passes; the test checks that the build exits with code 1 and that the reported critical problems, errors and warnings match the expected list. Removing a line from the expected list makes the test fail.
- **AC-002:** Temporarily disable one validation rule in Mordoc and run `npm test`: at least one test fails and shows the missing or extra problem lines. Undo the change afterwards.
- **AC-003:** In a fresh clone, `npm ci` and `npm test` run all validation tests and report the result, without a browser, within seconds.
