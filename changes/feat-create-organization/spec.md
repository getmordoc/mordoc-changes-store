# Mordoc organization on GitHub: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the organization, when either owner signs in, then they can manage its settings and repositories.
- **AC-002:** Given a moved repository, when someone opens its old address, then they arrive at the repository in the organization.
- **AC-003:** Given a moved repository, when an owner pushes a branch and opens a pull request, then it works as before.
- **AC-004:** Given the documentation site, when a visitor opens it after the move, then it is online, and it updates when a change is merged.
- **AC-005:** Given the Mordoc packages, when someone installs them after the move, then they work as before.
- **AC-006:** Given the main branch of a repository, when someone pushes to it directly, then the push is refused.

## Functional Requirements
- **FR-001:** Mordoc has its own organization on GitHub, with both owners as owners and a short description. The same name is claimed on npm.
- **FR-002:** The code, documentation, app starter and change documents repositories are in the organization, with their history, issues and pull requests.
- **FR-003:** Links to the repositories point to their new addresses: in the repositories, in the documentation and in the package information.
- **FR-004:** The documentation site stays online and keeps updating after the move.
- **FR-005:** Changes reach the main branch of every repository only through pull requests. A pull request does not need an approval before it is merged.

## Non-Functional Requirements
- **NFR-001:** Everything that works today keeps working: installing the packages, building the sites, pushing branches and opening old links.

## Boundaries
- The package names on npm stay the same, because people already install them by those names.

## Constraints
- The organization uses GitHub's free plan.
- The organization is created from the account that owns the repositories today, because only that account can move them.

## Risks
- The documentation site's hosting is connected to the repository, and may need to be connected again after the move.
- Old addresses only keep redirecting as long as nobody creates a repository with the same name on the old account.

## Open Issues
- None
