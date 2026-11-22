# Release Mordoc with one click: QA Plan

**Change:** `chore-release-workflow`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Check the workflow files with `actionlint` before each push.
- The workflows only run on GitHub, so they are tested there: the labels on the first pull request after the merge, the full release with the first new version, 2.1.0, and the stop check right after it.
- The tests on pull requests (`test.yml`) keep working as before.

## Test Coverage
- **AC-001:** After the merge, "Create release" shows a "Run workflow" button on the Actions tab; started on another branch, the job is skipped.
- **AC-002:** The first release, 2.1.0, is on npm with provenance pointing to the release run and its commit, and installs with `npm install mordoc@2.1.0`.
- **AC-003:** Release `v2.1.0` exists with tag `v2.1.0` on the released commit, and its notes list the pull requests since `v2.0.0`, grouped by type. The first pull request opened after the merge gets the label of its branch prefix.
- **AC-004:** After release 2.1.0, started again before the version is raised, the release stops before the tests with a message that 2.1.0 exists, and nothing new is on npm or GitHub. A failing test stops it before publishing, verified by reading the job's step order.
- **AC-005:** After the next release, 2.2.0, branch `chore-bump-version-to-2.3.0` exists and changes only `package.json` and `package-lock.json` to 2.3.0; the pull request opened from it runs the tests and gets the `chore` label.
