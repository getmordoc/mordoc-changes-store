# Release Mordoc with one click: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, in `.github/`.
- **FR-001:**
  - `.github/workflows/release.yml`, named "Create release", starts on `workflow_dispatch` and runs only on `refs/heads/main`.
  - The version is read from `package.json`; the tag is `v<version>`.
- **FR-002:**
  - The job runs `npm ci`, installs Playwright's Chromium and runs `npm test`.
  - `npm publish` runs after the tests.
  - `gh release create v<version> --target <commit> --title v<version> --generate-notes` runs after `npm publish`.
- **FR-003:**
  - Before the tests, the job stops when tag `v<version>` exists on GitHub or `mordoc@<version>` exists on npm.
  - `concurrency` lets one release run at a time.
- **FR-004:**
  - `.github/workflows/label.yml` runs on `pull_request_target` and labels each pull request with `actions/labeler`.
  - `.github/labeler.yml` maps the branch prefixes `feat-`, `fix-`, `refactor-`, `perf-`, `test-`, `docs-` and `chore-` to labels of the same names.
- **FR-005:**
  - `.github/release.yml` groups the generated notes by these labels, with the rest under "Other changes".
- **FR-006:**
  - After the release, the job runs `npm version minor --no-git-tag-version` on a branch `chore-bump-version-to-<next version>`, pushes it and opens a pull request with `gh pr create`.
- **NFR-001:**
  - The GitHub environment `release` allows deployments only from `main`, and the job runs in it.
  - The `mordoc` package on npm trusts `release.yml` in `getmordoc/mordoc`, environment `release`, as a trusted publisher.
  - The job has `id-token: write`, and publishes with npm 11.5.1 or later.
- **NFR-002:**
  - The job has `timeout-minutes: 15`.

## Decisions
- **D-001:** npm trusted publishing, because no token has to be stored or renewed, and npm adds provenance on its own. Rejected: an `NPM_TOKEN` secret.
- **D-002:** Publish to npm before the tag and release, because a failed publish then leaves nothing on GitHub. Rejected: tag and release first.
- **D-003:** Labels from the branch name with `actions/labeler`, because the branch names already carry the type and GitHub's release notes group by label. Rejected: labels added by hand.
- **D-004:** The version pull request is opened with the workflow's own token, because it only changes the version number, which the release just tested. GitHub runs no workflows on such a pull request; closing and reopening it runs the tests. Rejected: a GitHub App or personal token.
- **D-005:** The GitHub environment `release`, limited to `main`, because a workflow can be started on any branch and its own branch check can be removed there. Rejected: only the branch check in the workflow.
