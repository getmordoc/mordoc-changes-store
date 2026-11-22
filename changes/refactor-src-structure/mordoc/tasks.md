# Clearer code structure: Tasks

**Change:** `refactor-src-structure`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-006):** Let the build script clear `dist/` before compiling.
- [x] **T-002 (FR-001):** Move `pipeline.ts`, `utils/reporter.ts` and `config/` to `core/`.
- [x] **T-003 (FR-001):** Move `content/` to `core/content/` with its new file names, including `validation.ts`, and `diagrams/` to `core/content/diagrams/`.
- [x] **T-004 (FR-001):** Move `api/` to `core/openapi/`.
- [x] **T-005 (FR-003):** Move `scene.ts` to `types/` and `CONDITIONAL_BADGE` to `core/openapi/badges.ts`.
- [x] **T-006 (FR-004):** Split `markdoc-config.ts` into `core/content/schema/`: `index.ts`, one file per node in `nodes/` and one file per tag in `tags/`.
- [x] **T-007 (FR-001, FR-005):** Move the commands to `cli/dev/` and `cli/build/`, the shared Vite code to `cli/vite/`, with the package root one folder deeper in `paths.ts`, and let `bin/cli.js` call `cli/<command>/index.ts`.
- [x] **T-008 (FR-001):** Move the browser code in `app/` to `components/`, `layout/`, `pages/` and `openapi/`.
- [x] **T-009 (FR-002):** Let `app/tsconfig.json` include only `../types`, and check that each folder imports only from the folders it may use.
- [x] **T-010 (FR-001):** Update comments that name a file or folder to its new path.
