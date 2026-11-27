# One report for the problems in the content: QA Plan

**Change:** `refactor-build-report`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Build tests in `test/build/validation.test.ts` build the test sites in `test/build/` and compare the printed problems with the site's `expected.txt`.
- The preview test runs `mordoc dev` on a temporary copy of `test/build/errors/`, because it changes files. It waits for the line that Mordoc prints after each list, never for a time.
- `npm test`.

## Test Coverage
- **AC-001:** `test/build/errors/` is in `en`, `de` and `fr`, so its pages are also shown in German and French: `mordoc build` prints each line of `expected.txt` once, and stops. This test fails without the fix, following steps 1 and 2 to reproduce.
- **AC-002:** `test/build/missing-api/` has `{% banner %}Text{% /banner %}` in `content/en/index.md` and an API in `config/api.yaml` whose OpenAPI file doesn't exist: `mordoc build` prints the problem of the page and the error for the OpenAPI file in one list, without a stack, and stops. With `--verbose`, the error has its stack. This test fails without the fix, following step 3 to reproduce.
- **AC-003:**
  - The preview of `test/build/errors/` prints the same problems as `mordoc build` once when it starts.
  - After `content/en/unknown-tag.md` is saved with a second unknown tag, the preview prints the two problems of that page once.
  - After an API whose OpenAPI file doesn't exist is added to `config/api.yaml`, the preview prints the problems and the error for the OpenAPI file once, in one list, and keeps running.
