# Run the tests for every pull request: Tasks

**Change:** `chore-ci-tests`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-001):** Add `.github/workflows/test.yml`, which runs `npm test` with Chromium on pull requests into `main`, with read-only permission.
- [x] **T-002 (FR-002):** Let the workflow also run on pushes to `main`.
- [x] **T-003 (FR-003):** Keep the workflow to one job, `test`.
