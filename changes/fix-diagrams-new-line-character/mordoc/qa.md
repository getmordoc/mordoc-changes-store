# Break the actor name onto a new line in sequence diagrams: QA Plan

**Change:** `fix-diagrams-new-line-character`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Unit tests for the sequence diagram parser and layout, next to the existing ones.
- A check of a built diagram in the browser, in light and dark; the existing diagram tests keep passing.
- `npm run check` and `npm test`.

## Test Coverage
- **AC-001:** Parse `actor browser as "Merchant client \nBrowser"`: the actor has the lines `Merchant client` and `Browser`, and the drawn header text has no `\n` characters. This test fails without the fix, following the steps to reproduce.
- **AC-002:** In the built diagram, a two-line and a three-line actor name show all lines, without overlapping the icon or the first message.
- **FR-001:** Spaces around `\n` are trimmed; a name without `\n` gives one line; an actor without a declared name gives its id as the only line.
- **FR-002:** The header height grows with the longest actor name, and the lifelines and messages start below it.
- **NFR-001:** A diagram without `\n` in an actor name gives the same layout as before, with the header at the theme's `headerHeight`.
