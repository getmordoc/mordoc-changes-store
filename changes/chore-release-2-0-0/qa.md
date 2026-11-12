# Release Mordoc 2.0.0: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Before publishing: build mordoc-docs, the components example site and mordoc-api-demo with local Mordoc `main`; each finishes with no problems reported.
- After publishing: check npm, GitHub and a fresh install, with real internet.

## Test Coverage
- **AC-001:** `npm view mordoc version` shows `2.0.0`; a new site from `npx create-mordoc-app` has `"mordoc": "^2.0.0"` and builds.
- **AC-002:** `git ls-remote --tags origin v2.0.0` points to the same commit as `npm view mordoc@2.0.0 gitHead`, and `package.json` there says `2.0.0`.
- **AC-003:** Open the changelog in English and German in Chrome: the 2.0.0 entry is at the top, lists the new, changed and upgrade items from FR-002, and every link opens.
- **AC-004:** In mordoc-docs on the branch, `npm install` installs Mordoc 2.0.0 from npm; `npm run build` finishes with no problems reported, and the changelog and image pages show no console errors in Chrome.
- **AC-005:** A new folder with `"mordoc": "^1.9.1"`, after `npm install`, has Mordoc 1.9.1 installed.
