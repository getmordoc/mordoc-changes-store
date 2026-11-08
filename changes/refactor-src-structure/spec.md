# Clearer code structure: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the finished change, when Mordoc is compiled, then it succeeds with no errors.
- **AC-002:** Given all four example sites, when they are built before and after the change, then they produce the same pages.
- **AC-003:** Given the themes example site running in development, when someone edits a page or the navigation, then the change appears with no restart.
- **AC-004:** Given the finished change, when someone looks through the code and the compiled output, then they find only the new structure.
- **AC-005:** Given the dependency rules, when the code is checked, then every part follows them.
- **AC-006:** Given a moved file, when someone looks at its history, then they see the changes from before the move.

## Functional Requirements
- **FR-001:** A contributor finds all code in a small number of clearly named areas, as set out in the [plan](./plan.md).
- **FR-002:** Each area depends only on the areas it is allowed to use.
- **FR-003:** Shared type definitions are kept separate from code that runs.
- **FR-004:** Authors can use the same components as before.
- **FR-005:** Mordoc users run the same commands, with the same options and output as before.
- **FR-006:** The Mordoc package people install contains only the new structure.

## Non-Functional Requirements
- **NFR-001:** Generated sites stay the same.
- **NFR-002:** The history of every file is kept.
- **NFR-003:** Building a site takes about the same time as before, within 10%.

## Boundaries
- None

## Constraints
- None

## Risks
- This conflicts with open pull requests that touch the same code.
- It assumes nobody relies on Mordoc's internal files, only on its commands.
- It assumes custom themes use the documented theme settings, and don't depend on generated internal names.

## Open Issues
- Confirm the new folder names. The options are in the [plan](./plan.md).
- Agree with the maintainer before starting.
