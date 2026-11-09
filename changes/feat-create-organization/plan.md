# Mordoc organization on GitHub: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- Repositories to move, in this order: `mordoc-changes-store`, `mordoc-docs`, `create-mordoc-app`, `mordoc`. All are on the `shiva-varanasi` account today.
- **FR-001:**
  - The organization exists on the free plan, created from the `shiva-varanasi` account, with a profile description.
  - `siebeprojects` is an owner of the organization.
  - An npm organization with the same name exists, with both owners as members.
- **FR-002:**
  - Each repository is moved with GitHub's "Transfer ownership", one at a time, in the order above.
  - Every local clone's `origin` points to the new address.
- **FR-003:**
  - `mordoc/package.json` has a `repository` field with the new address, and the `repoitory` typo is fixed.
  - `create-mordoc-app/package.json` has the new `repository` address.
  - The components example site's footer, the `references/github-repo.md` and `writing-content/links.md` pages of `mordoc-docs` (English and German), and the store's pull request template use the new addresses.
  - The next npm releases of `mordoc` and `create-mordoc-app` carry the new addresses.
- **FR-004:**
  - The Vercel project of `mordoc-docs` is connected to the repository in the organization, and the Vercel GitHub app has access to the organization.
- **FR-005:**
  - Every repository has a ruleset on `main` that requires a pull request, with no required approvals and no bypass.

## Decisions
- **D-001:** Move the repositories with GitHub's transfer, because it keeps history, issues, pull requests and stars, and redirects the old addresses. Rejected: creating new repositories and pushing the code.
- **D-002:** Move the change documents repository first, because it has the least risk and tests the steps. Rejected: moving all repositories at once.
