# One report for the problems in the content: QA Plan

**Change:** `refactor-build-report`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Build tests in `test/build/report.test.ts` run `mordoc build` and `mordoc dev` on sites that the tests write in a temporary folder, and compare the printed problems.
- The existing build test in `test/build/validation.test.ts` keeps passing: the pages and the texts for the API reference are listed in one list.
- `npm test`.

## Test Coverage
- **AC-001:** A site in `en`, `de` and `fr` with `{% banner %}Text{% /banner %}` in `content/en/page.md`: `mordoc build` prints "Mordoc found 1 problem in your content:" and the line `content/en/page.md:5  critical  Undefined tag: 'banner'` once, and stops. This test fails without the fix, following steps 1 and 2 to reproduce.
- **AC-002:** The same site, with an API in `config/api.yaml` whose OpenAPI file doesn't exist: `mordoc build` prints the line of the page problem before the error for the OpenAPI file, and stops. This test fails without the fix, following step 3 to reproduce.
- **AC-003:**
  - The preview of the site of AC-001 prints the same problem as `mordoc build` once when it starts.
  - After `content/en/page.md` is saved with a second unknown tag, the preview prints the two problems of that page once.
  - After `config/api.yaml` is saved with an OpenAPI file that doesn't exist, the preview prints the problems once, and keeps running.
