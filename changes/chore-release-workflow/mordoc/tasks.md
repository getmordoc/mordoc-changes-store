# Release Mordoc with one click: Tasks

**Change:** `chore-release-workflow`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-004):** Add `label.yml` and `labeler.yml`, so each pull request gets the label of its branch prefix.
- [x] **T-002 (FR-005):** Add `.github/release.yml`, grouping the generated release notes by these labels.
- [x] **T-003 (FR-001, FR-002, FR-003):** Add `release.yml`: start on main, stop when the version exists, test, publish to npm, then tag and release.
- [x] **T-004 (FR-006):** Let `release.yml` push a branch that raises the minor version.
- [x] **T-005 (NFR-001):** Limit the GitHub environment `release` to `main`.
- [x] **T-006 (NFR-001):** Set `release.yml` in `getmordoc/mordoc`, environment `release`, as trusted publisher of the `mordoc` package on npm.
