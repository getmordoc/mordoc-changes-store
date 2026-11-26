# One report for the problems in the content: Tasks

**Change:** `refactor-build-report`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [ ] **T-001 (FR-001): Add the build report**

  Add `BuildProblem` and `BuildReport` to `src/core/build-report.ts`. `BuildReport` collects problems, prints them under "Mordoc found N problems in your content:", one line each, and throws `ValidationFailedError` from `stopOnErrors()` when one is an error. Move `ValidationFailedError` to this file.

- [ ] **T-002 (FR-001, FR-003): Add Markdoc's results to the build report**

  Rename `src/core/content/validation.ts` to `src/core/content/content-validator.ts`, and update its imports. `ContentValidator` gets a `BuildReport` and adds each Markdoc result to it, with the line as editors count it. `runPipeline` creates a `BuildReport` and prints it. `applyMordocWatchBatch` creates one `BuildReport` for the pages saved together, gives it to each `reparsePage`, and prints it once.

- [ ] **T-003 (FR-001): Validate a page once, not for each language that shows it**

  In `transformContent`, don't validate an entry with `isFallback`.

- [ ] **T-004 (FR-002): Print the report also when another error stops the build**

  `runPipeline` runs the stages and prints the report in a `finally`. After that, it calls `stopOnErrors()` when `failOnContentErrors` is set.

- [ ] **T-005 (FR-003): Don't rerun a full run that failed in the preview**

  In `applyMordocWatchBatch`, rerun the full pipeline after a failed page or config update, and not after a failed full run, so the preview prints the list once.

- [ ] **T-006 (FR-001): Add helpers for build tests on written sites**

  Add `test/build/build-site.ts` with `createSite`, `write`, `build` and `startPreview`, so a test writes its site in a temporary folder and reads the problems that `mordoc build` and `mordoc dev` print.

- [ ] **T-007 (FR-001, FR-002): Test the report of the build**

  Write the build tests of AC-001 and AC-002 in `test/build/report.test.ts`.

- [ ] **T-008 (FR-003): Test the report of the preview**

  Write the preview tests of AC-003 in `test/build/report.test.ts`.
