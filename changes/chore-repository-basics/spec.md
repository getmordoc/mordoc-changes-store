# Repository basics: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given any Mordoc repository, when a visitor opens it, then it has a LICENSE file that names "The Mordoc Authors" as the copyright holder, and an AUTHORS file that lists the authors.
- **AC-002:** Given the AUTHORS file, when a visitor reads it, then it lists the authors' names and says it is the list of authors for copyright purposes, and nothing more.
- **AC-003:** Given the package details of Mordoc, create-mordoc-app and the API demo site, when a visitor looks at them, then the author is "The Mordoc Authors".
- **AC-004:** Given any Mordoc repository, when a visitor opens it on GitHub, then GitHub shows its license, a one-sentence description of what the repository is for and topics that describe it, and a repository that publishes a website links to it.
- **AC-005:** Given any Mordoc repository, when a visitor reads its README, then it says what the repository is and where the documentation is.

## Functional Requirements
- **FR-001:** Every repository has a LICENSE file that names "The Mordoc Authors" as the copyright holder; the code repositories keep their MIT terms.
- **FR-002:** Every repository has an AUTHORS file that lists the authors.
- **FR-003:** The packages name "The Mordoc Authors" as their author.
- **FR-004:** Every repository has a one-sentence description and topics on GitHub, written in the same style; a repository that publishes a website shows its address.
- **FR-005:** Every repository has a README that says what it is and where to find the documentation, in the same structure.

## Non-Functional Requirements
- None

## Boundaries
- The license terms themselves stay MIT for the code; only the copyright line changes.

## Constraints
- Shiva Varanasi, currently named as the copyright holder, agrees to the change before it is made.

## Risks
- None

## Open Issues
- Which license the API demo repository gets, for example CC BY 4.0 or MIT.
