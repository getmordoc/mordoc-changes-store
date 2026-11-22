# Keep dependencies up to date and editors consistent: QA Plan

**Change:** `chore-dependabot-editorconfig`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Dependabot only runs on GitHub, so it is checked there after the merge; "Check for updates" under Insights → Dependency graph → Dependabot starts a run without waiting a week.
- The editor settings are checked locally against every file in the repository.
- `npm test` keeps passing.

## Test Coverage
- **AC-001:** After the merge, Dependabot shows both entries without errors. Its first run opens one `npm` pull request with all minor and patch updates, raising the versions in `package.json`, a separate pull request for each major update, and one pull request for the actions; each has the label `chore` and runs the `test` check.
- **AC-002:** The dependency graph, Dependabot alerts and Dependabot security updates are on under Settings → Advanced Security; each alert under Security → Dependabot has a pull request with its fix.
- **AC-003:** Every text file in the repository uses LF line endings, two-space indentation and ends with an empty line, so saving it in an editor that reads `.editorconfig` changes nothing.
