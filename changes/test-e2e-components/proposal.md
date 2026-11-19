# Browser tests for the components example site

## Description
As a Mordoc contributor, I want browser tests that check every component and interaction on the components example site, so that I know a change to Mordoc doesn't break what readers see.

## Why
- Mordoc's tests only check content validation; nothing checks what readers see.
- The [components example site](../feat-examples-components/proposal.md) shows every component, but nothing checks that they keep working.

## What
- Tests for the components example site, which check that each component works in both the light and the dark theme.
- The test tool and a command that runs only the browser tests. The tests for the other example sites reuse them.
- One command that runs all of Mordoc's tests, for example for every pull request.
