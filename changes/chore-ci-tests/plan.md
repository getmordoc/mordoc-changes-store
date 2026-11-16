# Run the tests for every pull request: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in the `mordoc` repository.
- **FR-001:**
  - `.github/workflows/test.yml` runs on `pull_request` into `main`.
  - The workflow installs Node from `.nvmrc`, runs `npm ci`, installs Chromium with `npx playwright install --with-deps chromium`, and runs `npm test`.
  - The workflow has only `contents: read` permission.
- **FR-002:**
  - `.github/workflows/test.yml` also runs on `push` to `main`.
- **FR-003:**
  - The workflow has one job, `test`, so its result shows as one check on the pull request and the commit.

## Decisions
- **D-001:** Trigger on `pull_request`, because it runs a fork's code without secrets or write access. Rejected: `pull_request_target`, which gives a fork's code access to them.
- **D-002:** Run on Linux only, because it is the fastest and the tests don't depend on the operating system. Rejected: also macOS and Windows.
- **D-003:** Run `npm test`, so CI and contributors use the same command. Rejected: separate steps per test suite in the workflow.
