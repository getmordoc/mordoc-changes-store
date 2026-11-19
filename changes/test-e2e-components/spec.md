# Browser tests for the components example site: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** Given the built components example site, when the browser tests run, then they pass only if every component on each page is shown with its content, in the light and the dark theme.
- **AC-002:** Given an interactive component, when a test uses it as a reader does, then the test passes only if the component responds as expected.
- **AC-003:** Given a change that breaks a component, when the browser tests run, then at least one test fails and names the page and the component.
- **AC-004:** Given a fresh copy of the repository, when a contributor runs the command for the browser tests, then the site is built and only the browser tests run and report the result.
- **AC-005:** Given a fresh copy of the repository, when a contributor runs the command for all tests, then the validation tests and the browser tests run and report the result.

## Functional Requirements
- **FR-001:** The tests open every page of the components example site and check that each component on it is shown with its content: hero, section, card and card grid, button, callout, accordion, columns, code block, link, heading and table, image, advanced image, diagram, clip and video embed.
- **FR-002:** The tests use the interactive parts as a reader does:
  - Open and close an accordion, and see that only one accordion in a group is open.
  - Enlarge and close an advanced image and a diagram.
  - Play and pause a clip.
  - Copy a code block and the link of a heading.
  - Jump to a heading from the table of contents.
  - Switch between the light and the dark theme.
- **FR-003:** Every test runs in both the light and the dark theme.
- **FR-004:** One command builds the site and runs only the browser tests.
- **FR-005:** One command runs all of Mordoc's tests: the validation tests and the browser tests.

## Non-Functional Requirements
- **NFR-001:** The tests check the site as it is built for publishing, with real embedded videos; nothing is replaced.
- **NFR-002:** The tests run on macOS, Linux and Windows, so they can later run for every pull request.
- **NFR-003:** The browser tests finish within two minutes.

## Boundaries
- None

## Constraints
- The browser for the tests is downloaded once, in addition to the npm packages.

## Risks
- The embedded videos come from an external service, so a test can fail when that service can't be reached.

## Open Issues
- None
