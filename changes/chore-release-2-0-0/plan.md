# Release Mordoc 2.0.0: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- Work in two repos: mordoc (the release) and mordoc-docs (the changelog and the move to 2.0.0, on a branch `chore-release-2-0-0`).
- **FR-001:**
  - mordoc `package.json` has `"version": "2.0.0"`, committed by `npm version major` on `main`.
  - The tag `v2.0.0` on that commit is pushed to GitHub.
  - `mordoc@2.0.0` is published to npm from that commit, with `latest` pointing to it.
- **FR-002:**
  - `content/en/change-log/2026.md` and `content/de/change-log/2026.md` start with a section for the release date, with `### Version 2.0.0` and the new, changed and upgrade items from FR-002, linking to the pages on content validation, code blocks, advanced images and landing pages.
- **FR-003:**
  - mordoc-docs `package.json` has `"mordoc": "^2.0.0"` and `"version": "2.0.0"`, with `package-lock.json` updated by `npm install`.

## Decisions
- **D-001:** Release as 2.0.0, because sites that built with 1.9.1 can stop building or look different. Rejected: 1.10.0, which `^1.9.1` would install without anyone choosing to upgrade.
- **D-002:** The changelog and the move to 2.0.0 go in one mordoc-docs pull request, merged right after publishing, because the documentation only builds correctly with 2.0.0. Rejected: merging the changelog before the release.
- **D-003:** mordoc-docs keeps its own version and sets it to 2.0.0, so it matches the Mordoc version it documents. Rejected: removing it.
