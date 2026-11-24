# Break the actor name onto a new line in sequence diagrams: Tasks

**Change:** `fix-diagrams-new-line-character`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [ ] **T-001 (FR-001):** Split the actor label at `\n` in `parser.ts`, and draw the actor header text with its lines in `layout.ts`.
- [ ] **T-002 (FR-002):** Make the header height fit the actor name with the most lines, keeping `headerHeight` as the minimum.
- [ ] **T-003 (FR-001, FR-002):** Add the parser and layout tests, and check the built diagram in the browser.
