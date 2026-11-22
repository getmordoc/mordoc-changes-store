# Remove the duplicate language helpers: QA Plan

**Change:** `refactor-remove-duplicate-lang-utils`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Nothing a user or author sees may change, including the `lang` of fallback pages.
- Neither site has fallback pages, so test on copies of them outside the repository: in the copy of `../mordoc-docs` delete half of the German pages except `index.md`, and in the copy of `../mordoc-api-demo` add `de` to `config/language.json` with only `content/de/index.md`.
- Before the first task, build both copies on `main` with `node <mordoc>/bin/cli.js build` and keep their `dist/` as the baseline.
- After each task: `npm run build` and `npm test`.

## Test Coverage
- **AC-001:** `npm run build` compiles with no errors.
- **AC-002:** Build both copies again and compare each `dist/` with the baseline: the same files, with the same content, including the `<html lang>` of translated and fallback pages.
- **AC-003:** `lang-utils` exists only in `src/app/`, and no file in `src/cli/` or `src/core/` imports from `app/`.
- **AC-004:** `npm test` passes, locally and in the pull request's `test` check.
