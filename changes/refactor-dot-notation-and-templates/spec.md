# Write property access and strings the usual way: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** A contributor finds properties read with a dot and strings built with template literals everywhere in the code.
- **AC-002:** A contributor's code check fails on a property read with brackets and a fixed name, on strings joined with `+`, and on a `switch` case that does nothing.

## Functional Requirements
- **FR-001:** A property with a fixed, valid name is read with a dot; brackets stay for names in a variable and names that aren't valid identifiers.
- **FR-002:** Strings that combine text and values use template literals.
- **FR-003:** A `switch` has no case that only repeats what its default does.
- **FR-004:** The code check reports each of these as a problem that fails it.

## Non-Functional Requirements
- **NFR-001:** Mordoc behaves the same: the same pages, the same messages, the same output.

## Boundaries
- None

## Constraints
- None

## Risks
- The change touches about 200 lines in the OpenAPI and configuration code, so it can conflict with open pull requests there.

## Open Issues
- None
