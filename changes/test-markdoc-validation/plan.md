# Tests for content validation: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in the `mordoc` repository.
- A `test/` folder holds all of Mordoc's tests, with the validation tests and their test site under `test/build/`.
- **FR-001:**
  - A minimal test site with one page per mistake, and a list of the problems it is expected to report.
  - The site has an API with an enrichment file that contains a mistake.
- **FR-002:**
  - A test file that builds the test site with the Mordoc command line, checks that the build stops, and compares the reported problems with the expected list, regardless of their order.
- **FR-003:**
  - `package.json` has a `test` script that builds Mordoc and runs every test file under `test/`.

## Decisions
- **D-001:** Use Node's built-in test runner, because Node 24 has it and it adds no dependency. Rejected: Vitest or Jest.
- **D-002:** Keep the test site with the tests, because it contains deliberate mistakes and is not an example to follow. Rejected: an example site under `examples/`.
- **D-003:** Compare whole problem lines with an expected list, because it checks the file, line, level and message at once and shows the difference when a test fails. Rejected: checking only the number of problems.
- **D-004:** Use one test site for critical problems, errors and warnings, because one build reports every problem. Rejected: a separate test site per level, and checking that the example sites build without problems, which the browser tests will cover.
