# Clearer code structure: QA Plan

**Change:** `refactor-src-structure`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Code is only moved and renamed, so nothing a user or author sees may change: the same pages, the same validation messages and the same commands.
- Before the first task, build the three sites on `main` and keep their `dist/` and build times as the baseline: `examples/components`, `../mordoc-docs` and `../mordoc-api-demo`, each with `node <mordoc>/bin/cli.js build`.
- After each task: `npm run build` and `npm test`.
- Generated CSS class names and asset file names contain a hash of the file's path, so they change when files move; the comparison of `dist/` replaces them with a placeholder first.

## Test Coverage
- **AC-001:** `npm run build` compiles with no errors.
- **AC-002:** Build the three sites again and compare each `dist/` with the baseline, after replacing generated class names and asset hashes: the same files, with the same content.
- **AC-003:** Run `mordoc dev` in `../mordoc-docs`, edit a page and the navigation: each change shows in the browser without a restart.
- **AC-004:** No old folder or file name is found in `src/`, `bin/`, comments included, or in the compiled `dist/`; `npm pack --dry-run` lists only the new structure, and a clean `npm run build` leaves no old files in `dist/`.
- **AC-005:** Search the imports of each folder: each imports only from the folders it may use. `app/tsconfig.json` includes only `../types`, and type-checking `app/` passes.
- **AC-006:** `git log --follow` on moved files, such as `core/content/schema/tags/callout.ts` and `app/components/callout/Callout.tsx`, shows their history from before the move.
- **AC-007:** `npm test` passes, locally and in the pull request's `test` check, with no change to the tests.
- **NFR-003:** The build times of the three sites are within 10% of the baseline.
