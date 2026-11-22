# Run the tests for every pull request

## Description
As a Mordoc maintainer, I want all tests to run on their own for every pull request into `main` and for `main` itself, so that I see whether a change breaks Mordoc before and after it is merged.

## Why
- The validation tests (`test-markdoc-validation`) and the browser tests (`test-e2e-components`) only run when a contributor remembers to run them.
- A pull request can break Mordoc without anyone noticing until later.

## What
- All tests run when a pull request into `main` is opened or updated, and the result shows on the pull request.
- All tests run again on `main` after a pull request is merged.
