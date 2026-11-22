# Lint and format the code: QA Plan

**Change:** `chore-lint-and-format`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Before the first task, build `examples/components` on `main` and keep its `dist/` as the baseline; formatting and fixes may not change the generated site.
- Try each check with a deliberate mistake in a copy of a file, and remove it afterwards.
- After each task: `npm run build` and `npm test`.

## Test Coverage
- **AC-001:** `npm run check` passes on the finished code, and reports an unused import, a hook inside a condition, a missing hook dependency and an unformatted line, each with its file and line.
- **AC-002:** `npm run fix` formats an unformatted file and removes an unused import; a hook inside a condition stays and is listed with its file and line.
- **AC-003:** With a deliberate mistake, `npm test` stops at the check; the pull request's `test` check shows `npm run check` in its log and passes on the finished code.
- **AC-004:** `npm run fix` on the finished code changes nothing; on GitHub, the history of a formatted file skips the formatting commit; `examples/components` builds the same pages as the baseline, with the accessibility fixes as the only differences.
- **NFR-001:** `npm run check` on all files takes at most 5 seconds.
