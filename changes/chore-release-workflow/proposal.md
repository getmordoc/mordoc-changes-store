# Release Mordoc with one click

## Description
As a Mordoc maintainer, I want to release a new version with one click, so that every release is tested, published and documented the same way.

## Why
- A release is done by hand: setting the version, running the tests, publishing to npm, and adding a tag and a release on GitHub. Steps get forgotten: versions 1.9.1 and 2.0.0 had no tag until later.
- Nobody can see what each version contains.
- Every version on npm is tested and can be traced back to the code it was built from, and maintainers spend less time on releases.

## What
- A release action on GitHub that tests the main branch, publishes the version to npm, and creates its tag and release.
- Release notes generated from the pull requests in the version, grouped by type.
- After a release, a branch that raises the minor version for the work that follows, ready for a pull request.
