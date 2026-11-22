# Tests for content validation: Tasks

**Change:** `test-markdoc-validation`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-003):** Add a `test` script to `package.json` that builds Mordoc and runs Node's test runner on every test file under `test/`.
- [x] **T-002 (FR-002):** Add the test file that builds a test site, checks the exit code and compares the reported problems with its expected list, regardless of their order.
- [x] **T-003 (FR-001):** Add the test site with one page per mistake and an API with an enrichment file that contains a mistake, and its expected list.
