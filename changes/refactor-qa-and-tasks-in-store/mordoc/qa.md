# Keep every document of a change in one folder: QA Plan

**Change:** `refactor-qa-and-tasks-in-store`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Check the branch's files and the pull request template; Mordoc's code doesn't change.
- `npm run check` and `npm test` keep passing.

## Test Coverage
- **AC-003:** On the branch, `changes/` doesn't exist and nothing else refers to it; the pull request template's Change section asks for the plain-text folder, with the example `mordoc-changes-store/changes/fix-accessibility/mordoc`; `npm run check` and `npm test` pass.
