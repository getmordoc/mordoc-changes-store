# One report for the problems in the content: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `src/core/build-report.ts` has a `BuildProblem` with an optional file, an optional line, a level and a message; a problem without a file is printed without a location.
  - `BuildReport` in that file collects the problems of one run, prints them under the heading "Mordoc found N problems in your content:", and throws `ValidationFailedError` from `stopOnErrors()` when one is an error.
  - `ValidationFailedError` moves from `src/core/content/validation.ts` to `src/core/build-report.ts`.
  - `src/core/content/validation.ts` is renamed to `src/core/content/content-validator.ts`.
  - `ContentValidator` in that file adds each Markdoc result to the run's `BuildReport`.
  - `transformContent` doesn't validate an entry with `isFallback`.
- **FR-002:**
  - `BuildReport.addLegacyError(error)` adds a thrown error as a problem without a file, with the level `error`, and with the error's stack instead of its message when the report is made with `verbose`.
  - `runPipeline` creates the `BuildReport` and runs the stages. When a stage throws, it adds the error with `addLegacyError`, prints the report, and stops with `ValidationFailedError`, also in the preview.
  - When no stage throws, `runPipeline` prints the report, and calls `stopOnErrors()` when `failOnContentErrors` is set.
- **FR-003:**
  - The page and config updates of `applyMordocWatchBatch` are in `applyTargetedUpdate`, which returns `false` when the batch needs the full pipeline.
  - `applyTargetedUpdate` creates one `BuildReport` for the pages saved together, gives it to each `reparsePage`, and prints it once.
  - `applyMordocWatchBatch` reruns the full pipeline after a failed update only when the update was a page or config update, not when it was already a full run.
  - When the full pipeline fails in the preview, the preview prints the error's message, and its stack only with `--verbose`.
  - When a page or config update fails in the preview, the preview prints nothing, because the full pipeline that follows lists the error, and prints the error with its stack only with `--verbose`.
  - `describeError(error, verbose)` in `src/core/build-report.ts` gives the message, or the stack with `verbose`, for `addLegacyError` and the preview.

## Decisions
- **D-001:** A fallback entry isn't validated, because it has the same text and config as the page in the default language. Rejected: removing repeated lines from the list.
- **D-002:** `runPipeline` catches the error of a stage and adds it to the report with `addLegacyError`, because every error that stops a run passes there, and the checks that throw don't have to change. Rejected: rewriting each check to add its problem to the report.
- **D-003:** The preview reruns the full pipeline only after a failed page or config update, because a full run that failed fails again and prints the list twice. Rejected: remembering which problems were printed.
- **D-004:** The report is in its own file, apart from Markdoc's validation, because the checks that follow aren't Markdoc's. Rejected: keeping it in `ContentValidator`.
- **D-005:** The stack is shown only with `--verbose`, because a thrown error doesn't say whether it's the author's mistake or a bug in Mordoc. Rejected: telling them apart by the error's type.
