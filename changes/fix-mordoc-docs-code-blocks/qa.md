# Mark the Mordoc documentation's Markdoc examples: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Build `mordoc-docs` from this change's branch with Mordoc's `main` (with content validation) and with the current release, and compare with `master`.
- Setup: Node.js 24. In the Mordoc repository on `main`, `npm run build`; in `mordoc-docs`, `node ../mordoc/bin/cli.js build` for Mordoc's `main` and `npm run build` for the current release.

## Test Coverage
- **AC-001:** Build with Mordoc's `main`: the build finishes and reports no problems.
- **AC-002:** In the build with Mordoc's `main`, compare every code block that shows Markdoc syntax with its source: each shows exactly what was written. Open the variables, landing pages and tables pages in Chrome, in English and German: the examples show as written and the console has no errors.
- **AC-003:** Build `master` and this branch with the current release: every built page is the same.
