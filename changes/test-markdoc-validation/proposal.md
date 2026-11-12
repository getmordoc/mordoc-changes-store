# Tests for content validation

## Description
As a Mordoc contributor, I want automated tests for content validation, so that I know every mistake is still reported correctly after each change to Mordoc.

## Why
- Content validation decides whether a site builds. If a rule breaks, broken pages can be published without anyone noticing.
- Today validation is only checked by hand.

## What
- Small test sites with deliberate mistakes, with only warnings, and with only correct content.
- Tests that build each test site and check what validation reports and whether the build stops.
- One command that runs these tests, and a folder for all of Mordoc's tests, next to the browser tests that come later.
- It builds on [content validation](../feat-markdoc-validation/proposal.md).
