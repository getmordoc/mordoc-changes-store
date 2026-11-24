# Break the actor name onto a new line in sequence diagrams: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, in `src/core/content/diagrams/sequence-diagram/`.
- **FR-001:**
  - `parser.ts` splits the actor label at `\n` and trims each part, the same way it does for message text (`.split('\n')`). The actor keeps its parts as `lines`.
  - `layout.ts` draws the actor header text with the actor's `lines` instead of `[actor.label]`.
- **FR-002:**
  - `layout.ts` takes the header height from the largest number of lines among the actors, using the line height the theme already uses for message text, instead of the fixed `headerHeight` of the theme.
  - The theme keeps `headerHeight` as the minimum, so a diagram without `\n` is unchanged.
- Tests in the existing sequence diagram parser and layout tests cover a name with `\n`, a name without it, and the header height.

## Decisions
- **D-001:** Split in the parser, not in the layout, because the parser already does it for messages, so both use one rule. Rejected: splitting in `layout.ts`, which leaves two places that know the `\n` rule.
- **D-002:** The header grows with the longest name instead of staying at the fixed height, because a second line would otherwise overlap the first message. Rejected: a fixed height for two lines, which wastes space in every diagram and still fails for three lines.
