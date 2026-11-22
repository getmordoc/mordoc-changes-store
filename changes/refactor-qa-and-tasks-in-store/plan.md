# Keep every document of a change in one folder: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc-changes-store` and `mordoc`.
- **FR-001:**
  - `changes/<change>/mordoc/qa.md` and `tasks.md` in the store for `chore-ci-tests`, `chore-dependabot-editorconfig`, `chore-lint-and-format`, `chore-release-workflow`, `fix-accessibility`, `fix-mobile-menu-after-resize`, `refactor-dot-notation-and-templates`, `refactor-remove-duplicate-lang-utils`, `refactor-src-structure`, `test-e2e-components` and `test-markdoc-validation`, with Mordoc's files.
- **FR-002:**
  - `changes/<change>/mordoc/qa.md`, moved with `git mv`, for `chore-release-2-0-0`, `chore-repository-basics`, `feat-change-examples-components-theme`, `feat-examples-components`, `feat-markdoc-validation`, `fix-landing-diagram-component` and `fix-markdown-image-error`.
  - `changes/<change>/mordoc-docs/qa.md`, moved with `git mv`, for `docs-image-pages` and `fix-mordoc-docs-code-blocks`.
- **FR-003:**
  - Each moved `qa.md` and `tasks.md` starts with `**Change:** \`<change>\``, followed by its link to `tasks.md` or `qa.md` when that file is next to it.
- **FR-004:**
  - The 12 links to other changes are the change's folder name in backticks.
  - The 10 plans with a `**QA plan:**` line have none.
- **FR-005:**
  - The README's "How a change is documented" has the folder tree of a change with a repository subfolder, in place of the sentence about the code repositories' `changes/` folders.
- **FR-006:**
  - Mordoc's `.github/pull_request_template.md` has `<The change's folder for Mordoc, such as "mordoc-changes-store/changes/fix-accessibility/mordoc">` under Change.
  - Mordoc has no `changes/` folder.

## Decisions
- **D-001:** A `qa.md` that covers several repositories goes to `mordoc/`, because those changes were led from Mordoc. Rejected: splitting it per repository, which rewrites history.
- **D-002:** Links to other changes become plain folder names, because the workflow names changes by folder name, and links break when folders move. Rejected: fixing the link paths.
- **D-003:** The store's pull request is merged before Mordoc's, so the documents are never missing. Rejected: merging both in any order.
