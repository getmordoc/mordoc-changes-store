# Mark the Mordoc documentation's Markdoc examples: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - In `mordoc-docs`, every fenced code block in `content/en/` and `content/de/` whose content contains `{%` has `{% process=false %}` after its language, such as ```` ```markdown {% process=false %} ````.

## Decisions
- **D-001:** Mark each code block with `{% process=false %}`, because that is how Markdoc shows a code block as written. Rejected: rewriting the examples so they contain no Markdoc syntax.
