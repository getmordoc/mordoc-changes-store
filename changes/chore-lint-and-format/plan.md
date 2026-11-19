# Lint and format the code: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, with Biome 2.6 as an exact `devDependency` and its settings in `biome.jsonc`.
- **FR-001:**
  - `biome.jsonc` checks every file that git tracks and Biome supports, with `vcs.useIgnoreFile`, except `.svg` and `.md` files.
  - The recommended rules are on, with `noUnusedVariables`, `noUnusedImports`, `useExhaustiveDependencies` and `useHookAtTopLevel` as errors; `useExhaustiveDependencies` reports missing dependencies only.
- **FR-002:**
  - The formatter uses `formatter.useEditorconfig`, single quotes, semicolons, trailing commas and a line width of 100.
- **FR-003:**
  - `package.json` has a `check` script, `biome ci --error-on-warnings`, and a `fix` script, `biome check --write`.
- **FR-004:**
  - The `test` script runs `check` first.
- **FR-005:**
  - One commit with only the output of `biome format --write`.
  - `.git-blame-ignore-revs` holds that commit's hash.
- **NFR-001:**
  - `npm run check` on all code takes at most 5 seconds.

## Decisions
- **D-001:** Biome, because it checks and formats in one tool and reads TypeScript itself, so TypeScript 7 works. Rejected: ESLint with typescript-eslint and Prettier, which needs two tools and doesn't support TypeScript 7 yet.
- **D-002:** A line width of 100, because 95% of the lines are 80 characters or shorter and only 183 are longer than 100, so formatting rewraps far fewer lines. Rejected: Biome's default of 80, which would rewrap 850 lines.
- **D-003:** Every error and warning is fixed in this change, in one commit after the formatting commit. Rejected: turning rules off or lowering them to information.
- **D-004:** Markdown left out, because Biome's Markdown formatter turns the frontmatter of Mordoc's pages into headings and doesn't know Markdoc tags. Rejected: formatting Markdown with Biome.
- **D-005:** The keyboard and screen reader problems in the language picker, search results and previews are marked with `biome-ignore` and fixed in `fix-accessibility`, because they change how readers use the site. Rejected: fixing them in this change.
