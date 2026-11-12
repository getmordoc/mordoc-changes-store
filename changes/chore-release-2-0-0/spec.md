# Release Mordoc 2.0.0: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given npm, when someone installs Mordoc, then they get version 2.0.0.
- **AC-002:** Given Mordoc on GitHub, when someone looks for version 2.0.0, then they find the exact code that was published.
- **AC-003:** Given the documentation's changelog, when a reader opens it, then the 2.0.0 entry lists what is new, what changed, and what to update when upgrading, in English and German.
- **AC-004:** Given the Mordoc documentation, when it is built with Mordoc 2.0.0, then the build finishes and reports no problems.
- **AC-005:** Given a site that depends on Mordoc 1.9.1 or a later 1.x version, when it installs its packages again, then it stays on version 1.

## Functional Requirements
- **FR-001:** Mordoc 2.0.0 can be installed, and its code can be found on GitHub by its version.
- **FR-002:** The changelog explains 2.0.0, in every language:
  - New: content validation, which lists every problem in your content and stops the build on errors; the advanced image, with a caption and click to enlarge; diagrams on landing pages.
  - Changed: a plain image no longer shows a caption or opens larger; variables in code blocks are filled in.
  - What to update: fix the problems the build reports; mark code blocks that show Markdoc syntax as written; use an advanced image where a caption or click to enlarge is wanted; use the hero and sections only on landing pages.
- **FR-003:** The Mordoc documentation uses Mordoc 2.0.0.

## Non-Functional Requirements
- None

## Boundaries
- Only the npm owner of Mordoc can publish it.

## Constraints
- The documentation for the 2.0.0 changes is merged before the release, and the documentation moves to 2.0.0 right after it is published.

## Risks
- Sites that upgrade without reading the changelog can stop building; the build lists each problem with its file and line.

## Open Issues
- How Mordoc is published today, and whether the release tag is created and pushed with it.
