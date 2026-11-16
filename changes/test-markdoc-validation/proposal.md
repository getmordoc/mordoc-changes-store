# Tests for content validation

## Description
As a Mordoc contributor, I want automated tests for content validation, so that I know every mistake is still reported correctly after each change to Mordoc.

## Why
- Content validation decides whether a site builds. If a rule breaks, broken pages can be published without anyone noticing.
- Today validation is only checked by hand.

## What
- A small test site with deliberate mistakes, at every level validation reports.
- Tests that build the test site and check what validation reports and whether the build stops.
- One command that runs these tests, and a folder for all of Mordoc's tests, next to the browser tests that come later.
- It builds on [content validation](../feat-markdoc-validation/proposal.md).
