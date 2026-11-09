# Mark the Mordoc documentation's Markdoc examples

## Description
As a Mordoc maintainer, I want the code blocks in the Mordoc documentation that show Markdoc syntax to be marked to be shown as written, so that the documentation builds once Mordoc validates all Markdoc content.

## Why
- Once Mordoc [validates all Markdoc content](../feat-markdoc-validation/proposal.md), the Mordoc documentation stops building: 62 code blocks in 18 files show Markdoc syntax, such as `{% $productName %}` or a callout, and Markdoc processes and validates them.

## What
- Each code block in the Mordoc documentation that shows Markdoc syntax is marked with `{% process=false %}`, so that it is shown as written.
- It is released together with Mordoc's content validation.
