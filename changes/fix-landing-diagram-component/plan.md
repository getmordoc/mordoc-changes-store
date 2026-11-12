# Diagrams on landing pages: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - The landing page renders with `contentComponents` plus `Hero` and `Section`.
- **FR-002:**
  - The components example site's `content/en/index.md` has a sequence diagram in a section.

## Decisions
- **D-001:** Build the landing page's components from the shared `contentComponents`, because the two lists then cannot grow apart again. Rejected: adding `Diagram` to the landing page's own list.
