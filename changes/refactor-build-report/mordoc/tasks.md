# One report for the problems in the content: Tasks

**Change:** `refactor-build-report`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-001): Add the build report**

  Add `BuildProblem` and `BuildReport` to `src/core/build-report.ts`. `BuildReport` collects problems, prints them under "Mordoc found N problems in your content:", one line each, and throws `ValidationFailedError` from `stopOnErrors()` when one is an error. Move `ValidationFailedError` to this file.

- [x] **T-002 (FR-001, FR-003): Add Markdoc's results to the build report**

  Rename `src/core/content/validation.ts` to `src/core/content/content-validator.ts`, and update its imports. `ContentValidator` gets a `BuildReport` and adds each Markdoc result to it, with the line as editors count it. `runPipeline` creates a `BuildReport` and prints it. `applyMordocWatchBatch` creates one `BuildReport` for the pages saved together, gives it to each `reparsePage`, and prints it once.

- [x] **T-003 (FR-001): Validate a page once, not for each language that shows it**

  In `transformContent`, don't validate an entry with `isFallback`.

- [x] **T-004 (FR-002): Print the report also when another error stops the build**

  `runPipeline` runs the stages and prints the report in a `finally`. After that, it calls `stopOnErrors()` when `failOnContentErrors` is set.

- [x] **T-005 (FR-003): Don't rerun a full run that failed in the preview**

  In `applyMordocWatchBatch`, rerun the full pipeline after a failed page or config update, and not after a failed full run, so the preview prints the list once.

- [x] **T-006 (FR-001): Test that each problem is listed once**

  Add `test/build/errors/config/language.json` with `en`, `de` and `fr`, so the existing build test of that site checks that each problem is printed once.

- [x] **T-007 (FR-002): Test the list when an OpenAPI file can't be loaded**

  Add the site `test/build/missing-api/` of AC-002 with its `expected.txt`, and a build test in `test/build/validation.test.ts` that checks the problem is printed before the OpenAPI error and the build stops.

- [x] **T-008 (FR-003): Test the problems in the preview**

  Add a test in `test/build/validation.test.ts` that copies `test/build/errors/` to a temporary folder, starts `mordoc dev` on it, and checks the problems of AC-003.
