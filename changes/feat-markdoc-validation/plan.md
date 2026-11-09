# Validate Markdoc content: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `transformContent` runs `Markdoc.validate()` on each page with the same config as `Markdoc.transform()`, before transforming it.
- **FR-002:**
  - Each problem is collected with the page's file path, its line, its level and its message.
  - Problems are printed as `file:line  level  message`.
- **FR-003:**
  - `mordoc build` stops after the content step when a problem has the level `error` or `critical`, with the number of problems.
- **FR-004:**
  - `reparsePage` prints the problems and does not stop.
- **FR-005:**
  - The `fence` node has the `process` attribute, as Markdoc's own `fence` node does.
  - The `fence` node builds its content from the transformed children when there are any, and from `content` otherwise, as Markdoc's own `fence` node does.
  - `CodeBlock` and `Diagram` receive that content.

## Decisions
- **D-001:** Process and check code blocks as Markdoc does, with `{% process=false %}` to show one as written, because that is how Markdoc works. Rejected: treating every code block as raw text.
- **D-002:** Stop the build on `error` and `critical`, and only report warnings, because some warnings may come from Mordoc's tag rules being too strict. Rejected: stopping on every problem.
