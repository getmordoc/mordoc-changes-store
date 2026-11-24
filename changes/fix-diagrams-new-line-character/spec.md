# Break the actor name onto a new line in sequence diagrams: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The reader sees an actor name with `\n` on separate lines, without the characters `\n`.
- **AC-002:** The reader sees the whole actor name, without it overlapping the actor icon or the first message.

## Functional Requirements
- **FR-001:** The actor name breaks onto a new line at each `\n`, like the text of a message does.
  - Spaces around the `\n` are not shown.
  - An actor name without `\n` shows as before.
  - An actor without a name declared shows its id as before.
- **FR-002:** The space for the actor name in the header fits the number of lines of the longest actor name in the diagram.
  - The lifelines and the messages start below the header.

## Non-Functional Requirements
- **NFR-001:** A diagram without `\n` in an actor name looks the same as before.

## Boundaries
- The syntax of the actor declaration and of the message stays as it is.
- Only `\n` as typed in the diagram text is a new line. Wrapping a long line automatically is not part of this fix.

## Constraints
- None

## Risks
- A header that grows with the number of lines moves everything below it, so existing diagrams must stay identical when no name has `\n`.

## Open Issues
- None
