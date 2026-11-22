# Keep every document of a change in one folder: QA Plan

**Change:** `refactor-qa-and-tasks-in-store`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Compare before and after: every `qa.md` and `tasks.md` from Mordoc and from the top of a change folder is in a repository subfolder, unchanged apart from its header and links.
- Check every relative link in the store with a script that follows each `](./…)` and `](../…)` and reports the ones that don't resolve.
- `git diff --stat -M` shows only moves, headers, links and the README.

## Test Coverage
- **AC-001:** Each of the 20 changes has its `qa.md`, and its `tasks.md` where there was one, in a repository subfolder; no change folder has a `qa.md` or `tasks.md` at its top.
- **AC-002:** The subfolders are `mordoc/` or `mordoc-docs/`, matching the repository each change was built in, and `mordoc/` for the two changes that cover several repositories.
- **AC-004:** The link check reports no broken links, and no link points into another change's folder.
