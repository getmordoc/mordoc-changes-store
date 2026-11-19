# Keep dependencies up to date and editors consistent: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`: `.github/dependabot.yml`, `.editorconfig` and the repository's settings on GitHub.
- **FR-001:**
  - `dependabot.yml` has an `npm` entry for `/`, with a `weekly` schedule and `versioning-strategy: increase`.
  - A group `minor-and-patch` holds the `minor` and `patch` updates; major updates are left out of the group.
- **FR-002:**
  - `dependabot.yml` has a `github-actions` entry for `/`, with a `weekly` schedule and one group for all actions.
- **FR-003:**
  - Under Settings → Advanced Security, the dependency graph, Dependabot alerts and Dependabot security updates are on.
- **FR-004:**
  - Both entries in `dependabot.yml` have `labels: [chore]`.
- **FR-005:**
  - `.editorconfig` has `root = true` and, for `[*]`, `indent_style = space`, `indent_size = 2`, `end_of_line = lf` and `insert_final_newline = true`.

## Decisions
- **D-001:** `versioning-strategy: increase`, because the lowest version in `package.json` is then the version the tests ran with. Rejected: the default, which for a package like Mordoc only updates `package-lock.json` while the version fits the range.
- **D-002:** The label `chore` set by Dependabot, because the labeler only knows branch prefixes such as `chore-`, and Dependabot's branches start with `dependabot/`. Rejected: a `dependabot/` rule in `labeler.yml`.
