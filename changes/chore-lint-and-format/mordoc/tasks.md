# Lint and format the code: Tasks

**Change:** `chore-lint-and-format`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-001, FR-002):** Add Biome 2.6 as an exact `devDependency`, and `biome.jsonc` with the files, rules and formatting.
- [x] **T-002 (FR-003, FR-004):** Add the `check` and `fix` scripts, and let `test` run `check` first.
- [x] **T-003 (FR-005):** Format all code with `npm run fix` in a commit of its own, and add its hash to `.git-blame-ignore-revs`.
- [x] **T-004 (FR-001):** Fix every error and warning the check reports, in one commit.
