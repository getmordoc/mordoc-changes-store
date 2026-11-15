# Release Mordoc 2.0.0

## Description
As a Mordoc user, I want a new major release with clear notes on what changed, so that I know what to update in my site before I upgrade.

## Why
- Since 1.9.1, Mordoc [validates all Markdoc content](../feat-markdoc-validation/proposal.md) and stops the build on errors, and [a plain image no longer has a caption or click to enlarge](../fix-markdown-image-error/proposal.md). Sites that built with 1.9.1 may stop building or look different, so this is a major release.
- Sites that depend on `^1.9.1` don't receive a major release automatically, so nobody upgrades by accident.

## What
- Mordoc 2.0.0 published on npm, with a release tag on GitHub.
- A 2.0.0 entry in the changelog of the Mordoc documentation, in English and German, with what changed and what to update when upgrading.
- The Mordoc documentation uses Mordoc 2.0.0.
