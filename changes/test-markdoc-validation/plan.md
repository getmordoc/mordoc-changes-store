# Tests for content validation: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- Directory structure:
```
test/
├── unit/                      later: unit tests
├── build/
│   ├── validation.test.ts
│   └── fixtures/
│       └── validation/
│           ├── errors/        site with one page per mistake, and expected.txt
│           ├── warnings/      site with only warnings, and expected.txt
│           └── clean/         site with only correct content
└── e2e/                       later: browser tests for the example sites
```
- **FR-001:**
  - `test/build/fixtures/validation/errors/` is a minimal Mordoc site with one page per mistake from FR-001.
  - `errors/expected.txt` lists each expected problem as `file:line  level  message`.
- **FR-002:**
  - `test/build/fixtures/validation/warnings/` is a minimal site with only warnings, and `warnings/expected.txt` lists them.
- **FR-003:**
  - `test/build/fixtures/validation/clean/` is a minimal site with only allowed content, and no `expected.txt`.
- **FR-004:**
  - `test/build/validation.test.ts` runs `bin/cli.js build` in each fixture with Node's built-in test runner, checks the exit code (1 for `errors`, 0 for `warnings` and `clean`), and compares the reported problem lines with `expected.txt`, regardless of their order.
- **FR-005:**
  - `package.json` has `"test": "npm run test:build"` and `"test:build"`, which runs `node --test` on `test/build/`.

## Decisions
- **D-001:** Use Node's built-in test runner, because Node 24 has it and it adds no dependency. Rejected: Vitest or Jest.
- **D-002:** Keep the test sites under `test/build/fixtures/`, because they contain deliberate mistakes and are not examples to follow. Rejected: an example site under `examples/`.
- **D-003:** Compare whole problem lines with an expected list, because it checks the file, line, level and message at once and shows the difference when a test fails. Rejected: checking only the number of problems.
