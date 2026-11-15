# Version strategy

## Description
As a Mordoc maintainer, I want one agreed way to choose and keep up to date the Node.js, npm, dependency and release versions in every Mordoc repository, so that users know what they need to run Mordoc and maintainers do not have to decide again with every change.

## Why
- The Node.js versions do not match across the repositories. mordoc requires Node.js 24.18.1 or later, create-mordoc-app still says Node.js 18 or later, and every repository's `.nvmrc` says 24. A new site therefore installs mordoc on Node.js versions that mordoc does not support, with only a warning during the install.
- Nobody knows why mordoc requires exactly 24.18.1. It came in with a dependency update, while mordoc's dependencies need Node.js 22.22 or later, and a new site still builds on Node.js 22.19.
- There is no rule for which part of a release number to raise. create-mordoc-app was first given 1.4.0 for a fix and then changed to 1.3.1 before it was published.
- There is no agreement on when the minimum versions are checked, so they are only noticed when something goes wrong, like the npm warning for fsevents.

## What
- A decision, written down in one place, for:
  - the minimum Node.js version Mordoc supports, and which Node.js version the repositories use for development;
  - the npm version the repositories use, and how lock files are kept up to date;
  - how dependency versions are written, such as `^` ranges, and when dependencies are updated;
  - which part of a release number is raised for which kind of change, for mordoc and create-mordoc-app.
- When these versions are checked again, such as with every major Mordoc release or when a Node.js version reaches its end of life.
- Every repository follows the decision: mordoc, mordoc-docs, create-mordoc-app and the sites create-mordoc-app makes, with the same minimum Node.js version wherever one is stated.
