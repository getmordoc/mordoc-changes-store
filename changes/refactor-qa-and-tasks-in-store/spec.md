# Keep every document of a change in one folder: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** A contributor finds all documents of every change in its folder in the store.
- **AC-002:** A contributor sees which repositories a change was built in, from its subfolders.
- **AC-003:** Mordoc has no `changes/` folder, and its pull requests name the change's folder as plain text.
- **AC-004:** A contributor finds no broken links in the store.

## Functional Requirements
- **FR-001:** The `qa.md` and `tasks.md` of the 11 changes in Mordoc's `changes/` folder move to the store, into the subfolder `mordoc/` of each change.
- **FR-002:** A `qa.md` at the top of a change folder in the store moves to the subfolder of the repository the change was built in. A `qa.md` that covers several repositories goes to the subfolder of the repository the change was led from.
- **FR-003:** Each moved `qa.md` and `tasks.md` names its change by folder name at the top, like the templates.
- **FR-004:** A change refers to another change by its folder name, as plain text. Links to the documents of other changes, and links to a `qa.md` that is no longer next to the plan, are removed.
- **FR-005:** The store's README shows the folder of a change with a subfolder for each repository.
- **FR-006:** Mordoc's pull request template asks for the change's folder for Mordoc as plain text, such as `mordoc-changes-store/changes/fix-accessibility/mordoc`.

## Non-Functional Requirements
- **NFR-001:** None

## Boundaries
- The text of the existing documents stays as it is, apart from their headers and links.

## Constraints
- The store and Mordoc change only through pull requests.

## Risks
- The parked branch `feat-modern-look-and-feel` in Mordoc and the Mordoc documentation still adds a `changes/` folder; it moves to the store when that change is picked up again.

## Open Issues
- None
