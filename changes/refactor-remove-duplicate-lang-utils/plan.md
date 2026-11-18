# Remove the duplicate language helpers: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001:**
  - `cli/build/ssg-runner.ts` sets the page's `lang` from `route.language`.
- **FR-002:**
  - `cli/build/lang-utils.ts` is deleted.
  - The comment at the top of `app/lang-utils.ts` says it imports only types from `types/`, and no longer refers to the deleted copy.

## Decisions
- **D-001:** `route.language`, because content discovery and the operation pages already set it to the language in the URL, fallback pages included. Rejected: the build importing `app/lang-utils.ts`, because `cli/` may not import from `app/`.
