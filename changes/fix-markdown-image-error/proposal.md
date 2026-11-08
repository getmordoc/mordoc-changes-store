# Markdown images cause a browser error

## Description
As a site reader, I want pages with images to load with no errors, so that the page works as intended.

## Why
- Every page with a Markdown image logs a browser error, although the image still shows. Reproduced on 2026-11-06 on the images page of the [components example site](../feat-examples-components/proposal.md).
- This must be fixed before the [browser tests for the components example site](../test-e2e-components/proposal.md), which check that pages load with no errors.

## What
- Pages with images load with no errors, and images look and behave as they do today.
