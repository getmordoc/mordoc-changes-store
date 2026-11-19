# Keep dependencies up to date and editors consistent

## Description
As a Mordoc maintainer, I want updates to Mordoc's packages and workflow actions proposed automatically, and every editor to use the same basic settings, so that Mordoc stays secure and contributions look the same on every computer.

## Why
- Package and action updates, including security fixes, are only noticed when someone looks for them.
- Editors use different indentation and line endings, especially on Windows, so files change without anyone meaning to.
- Fewer security issues for the people who use Mordoc, because its packages are updated regularly, and pull requests that contain only real changes.

## What
- Pull requests that propose updates to Mordoc's packages and GitHub actions, on a regular schedule, which the tests check like any other pull request.
- Shared editor settings for indentation, line endings and the end of each file, which most editors pick up on their own.
