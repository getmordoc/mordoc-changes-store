# One report for the problems in the content: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `src/core/build-report.ts` has a `BuildProblem` with a file, an optional line, a level and a message.
  - `BuildReport` in that file collects the problems of one run, prints them under the heading "Mordoc found N problems in your content:", and throws `ValidationFailedError` from `stopOnErrors()` when one is an error.
  - `ValidationFailedError` moves from `src/core/content/validation.ts` to `src/core/build-report.ts`.
  - `src/core/content/validation.ts` is renamed to `src/core/content/content-validator.ts`.
  - `ContentValidator` in that file adds each Markdoc result to the run's `BuildReport`.
  - `transformContent` doesn't validate an entry with `isFallback`.
- **FR-002:**
  - `runPipeline` creates the `BuildReport`, runs the stages, and prints the report in a `finally`.
  - `runPipeline` calls `stopOnErrors()` after the report is printed, when `failOnContentErrors` is set.
- **FR-003:**
  - `applyMordocWatchBatch` creates one `BuildReport` for the pages saved together, gives it to each `reparsePage`, and prints it once.
  - `applyMordocWatchBatch` reruns the full pipeline after a failed update only when the update was a page or config update, not when it was already a full run.

## Decisions
- **D-001:** A fallback entry isn't validated, because it has the same text and config as the page in the default language. Rejected: removing repeated lines from the list.
- **D-002:** The report is printed in a `finally` in `runPipeline`, because every error that stops a run passes there. Rejected: catching errors in each stage.
- **D-003:** The preview reruns the full pipeline only after a failed page or config update, because a full run that failed fails again and prints the list twice. Rejected: remembering which problems were printed.
- **D-004:** The report is in its own file, apart from Markdoc's validation, because the checks that follow aren't Markdoc's. Rejected: keeping it in `ContentValidator`.
