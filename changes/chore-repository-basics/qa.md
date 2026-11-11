# Repository basics: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Check each repository's files on its branch, and its GitHub page after merging. Compare the LICENSE and AUTHORS files with the texts in the plan.
- The code and its behavior must stay unchanged.

## Test Coverage
- **AC-001:** In every repository, open LICENSE and AUTHORS: LICENSE has the MIT text from the plan; AUTHORS has the text from the plan.
- **AC-002:** Read each AUTHORS file: it has the heading line and the authors' names, and nothing more.
- **AC-003:** In `package.json` of Mordoc, create-mordoc-app and the API demo site, the author is "The Mordoc Authors"; `npm pack --dry-run` of Mordoc includes the changed `package.json` and builds without errors.
- **AC-004:** Open each repository on GitHub: GitHub recognizes its license, and shows the description, the topics and, for the documentation and API demo, the website from the plan.
- **AC-005:** Read each README: it starts with the repository's name and the GitHub description, and links to https://mordoc.dev; every command in it works when followed.
