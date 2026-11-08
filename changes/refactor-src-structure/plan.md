# Clearer code structure: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)
**Tasks:** [tasks/](./tasks/)

## Approach
- Files are moved with `git mv`.
- Target structure:

| Folder | Role | May import from |
|---|---|---|
| `core/` | Builds `MordocData` from the docs project. Node.js only. | `types/` |
| `cli/` | The commands: run `core/`, Vite and the build steps, write `dist/`. | `core/`, `types/` |
| `app/` | Displays `MordocData` in the browser. | `types/` (types only) |
| `types/` | The contract: types of `MordocData`. No code. | — |

`←` marks where a file comes from.

```
src/
├── core/                               ── A. BUILDS MordocData FROM THE DOCS PROJECT (Node.js only, no Vite/React)
│   ├── pipeline.ts                     ← src/pipeline.ts
│   ├── reporter.ts                     ← utils/reporter.ts: progress output, used by core/ and cli/
│   ├── config/                         ← src/config/ (contents unchanged)
│   │   ├── assets-loader.ts
│   │   ├── footer-loader.ts
│   │   ├── header-loader.ts
│   │   ├── language-loader.ts
│   │   ├── sidenav-loader.ts
│   │   ├── site-loader.ts
│   │   ├── topnav-loader.ts
│   │   ├── translations-loader.ts
│   │   └── variables-loader.ts
│   ├── content/                        ← src/content/: Markdown pages → renderable trees
│   │   ├── diagrams/                   ← src/diagrams/: only called by nodes/fence.ts
│   │   │   ├── build-scene.ts
│   │   │   ├── generic/
│   │   │   │   └── diagram-definition.ts   (scene.ts moves to types/)
│   │   │   └── sequence-diagram/
│   │   │       ├── index.ts
│   │   │       ├── layout.ts
│   │   │       ├── parser.ts
│   │   │       └── theme.ts
│   │   ├── loader.ts                   ← content-loader.ts
│   │   ├── parse.ts                    ← content-parser.ts
│   │   ├── transform.ts                ← content-transformer.ts
│   │   ├── slug.ts
│   │   └── schema/                     ← split from markdoc-config.ts
│   │       ├── index.ts                createDefaultMarkdocConfig()
│   │       ├── nodes/                  overrides of standard Markdown syntax
│   │       │   ├── index.ts
│   │       │   ├── fence.ts
│   │       │   ├── heading.ts          (incl. extractText helper, only used here)
│   │       │   ├── image.ts
│   │       │   └── link.ts
│   │       └── tags/                   mordoc's {% %} tags
│   │           ├── index.ts
│   │           ├── accordion.ts
│   │           ├── accordions.ts
│   │           ├── button.ts
│   │           ├── callout.ts
│   │           ├── card.ts
│   │           ├── card-grid.ts
│   │           ├── clip.ts
│   │           ├── column.ts
│   │           ├── columns.ts
│   │           ├── hero.ts
│   │           ├── image.ts
│   │           ├── link.ts
│   │           ├── params.ts           (only used in API enrichment files, not by content authors)
│   │           ├── section.ts
│   │           └── video-embed.ts
│   └── openapi/                        ← src/api/: separate page source (config/api.yaml + spec)
│       ├── index.ts
│       ├── badges.ts                   ← CONDITIONAL_BADGE from types/api.ts (only used in openapi/)
│       ├── build-operation-views.ts
│       ├── curl-sample.ts
│       ├── diagnostics.ts
│       ├── enrichment-loader.ts
│       ├── enrichment-parser.ts
│       ├── examples.ts
│       ├── nav-check.ts
│       ├── registry-loader.ts
│       ├── schema-walk.ts
│       ├── slug.ts
│       └── spec-loader.ts
│
├── cli/                                ── B. THE MORDOC COMMANDS: build the website (Node.js + Vite)
│   │                                   bin/cli.js is only the entry point; it calls cli/<command>/index.ts.
│   ├── vite/                           shared by dev and build
│   │   ├── plugin.ts                   ← vite/plugin.ts
│   │   └── paths.ts                    ← utils/paths.ts (one level deeper: root path '../../..' → '../../../..')
│   ├── dev/                            mordoc dev
│   │   └── index.ts                    ← cli/dev.ts
│   └── build/                          mordoc build, and the steps only it uses
│       ├── index.ts                    ← cli/build.ts
│       ├── asset-rewrite.ts            ← cli/asset-rewrite.ts: copies config/assets → dist/_assets
│       ├── lang-utils.ts               ← utils/lang-utils.ts: only used by ssg-runner.ts
│       ├── pagefind-indexer.ts         ← cli/pagefind-indexer.ts: search index from the HTML
│       └── ssg-runner.ts               ← cli/ssg-runner.ts: renders every route to HTML
│
├── types/                              ── C. THE CONTRACT: types of MordocData, used by core, cli and app (types only)
│   ├── api.ts                          (CONDITIONAL_BADGE moves to core/openapi/badges.ts)
│   ├── assets.ts
│   ├── content.ts
│   ├── fonts.ts
│   ├── language.ts
│   ├── navigation.ts
│   ├── pipeline.ts
│   ├── scene.ts                        ← diagrams/generic/scene.ts
│   └── site.ts
│
└── app/                                ── D. THE WEBSITE (browser, shipped as source)
    ├── index.html
    ├── index.css
    ├── main.tsx
    ├── entry-server.tsx
    ├── App.tsx
    ├── App.module.css
    ├── routes.tsx
    ├── data-context.tsx
    ├── lang-utils.ts
    ├── path-utils.ts
    ├── globals.d.ts
    ├── virtual-modules.d.ts
    ├── vite-env.d.ts
    ├── tsconfig.json                   (include: ../types only)
    ├── assets/
    │   └── fonts/
    │       ├── InterVariable.woff2
    │       └── InterVariable-Italic.woff2
    ├── components/                     ← app/content/: what tags and nodes render to
    │   ├── Content.tsx                 ← content/Content.tsx
    │   ├── Content.module.css
    │   ├── Typography.module.css
    │   ├── component-map.ts
    │   ├── accordion/
    │   │   ├── Accordion.tsx
    │   │   ├── Accordion.module.css
    │   │   ├── Accordions.tsx
    │   │   ├── Accordions.module.css
    │   │   └── accordions-context.ts
    │   ├── button/                     ← content/landing/button/
    │   │   ├── Button.tsx
    │   │   └── Button.module.css
    │   ├── callout/
    │   │   ├── Callout.tsx
    │   │   └── Callout.module.css
    │   ├── card/
    │   │   ├── Card.tsx
    │   │   ├── Card.module.css
    │   │   ├── CardGrid.tsx
    │   │   └── CardGrid.module.css
    │   ├── clip/
    │   │   ├── Clip.tsx
    │   │   └── Clip.module.css
    │   ├── code-block/                 (fence node)
    │   │   ├── CodeBlock.tsx
    │   │   └── CodeBlock.module.css
    │   ├── columns/
    │   │   ├── Column.tsx
    │   │   ├── Column.module.css
    │   │   ├── Columns.tsx
    │   │   └── Columns.module.css
    │   ├── diagram/
    │   │   ├── Diagram.tsx
    │   │   ├── Diagram.module.css
    │   │   └── SceneSvg.tsx
    │   ├── heading/                    (heading node)
    │   │   ├── Heading.tsx
    │   │   └── Heading.module.css
    │   ├── hero/                       ← content/landing/hero/
    │   │   ├── Hero.tsx
    │   │   └── Hero.module.css
    │   ├── image/
    │   │   ├── Image.tsx
    │   │   └── Image.module.css
    │   ├── link/
    │   │   └── ContentLink.tsx
    │   ├── section/                    ← content/landing/section/
    │   │   ├── Section.tsx
    │   │   └── Section.module.css
    │   └── video-embed/
    │       ├── VideoEmbed.tsx
    │       ├── VideoEmbed.module.css
    │       └── providers.ts
    ├── layout/                         page frame
    │   ├── breadcrumb/                 ← app/breadcrumb/
    │   │   ├── Breadcrumb.tsx
    │   │   ├── Breadcrumb.module.css
    │   │   └── useBreadcrumb.ts
    │   ├── footer/                     ← content/footer/
    │   │   ├── Footer.tsx
    │   │   └── Footer.module.css
    │   ├── header/                     ← app/header/
    │   │   ├── Header.tsx
    │   │   ├── Header.module.css
    │   │   ├── HeaderLinks.tsx
    │   │   ├── HeaderLinks.module.css
    │   │   ├── LanguagePicker.tsx
    │   │   ├── LanguagePicker.module.css
    │   │   ├── SearchBar.tsx
    │   │   ├── SearchBar.module.css
    │   │   ├── SearchModal.tsx
    │   │   ├── SearchModal.module.css
    │   │   ├── ThemeToggle.tsx
    │   │   ├── ThemeToggle.module.css
    │   │   ├── Topnav.tsx
    │   │   ├── Topnav.module.css
    │   │   └── useTheme.ts
    │   ├── sidenav/                    ← app/sidenav/
    │   │   ├── Sidenav.tsx
    │   │   └── Sidenav.module.css
    │   └── toc/                        ← content/toc/
    │       ├── Toc.tsx
    │       └── Toc.module.css
    ├── pages/                          ← from app/content/
    │   ├── article/
    │   │   ├── ArticlePage.tsx
    │   │   └── ArticlePage.module.css
    │   ├── landing/
    │   │   ├── LandingPage.tsx
    │   │   └── LandingPage.module.css
    │   ├── not-found/
    │   │   ├── NotFound.tsx
    │   │   └── NotFound.module.css
    │   ├── route-error/
    │   │   ├── RouteError.tsx
    │   │   └── RouteError.module.css
    │   └── skeleton/
    │       ├── Skeleton.tsx
    │       └── Skeleton.module.css
    ├── openapi/                        ← app/api/: displays the pages built by core/openapi/
    │   ├── Endpoint.tsx
    │   ├── Endpoint.module.css
    │   ├── ExamplePanel.tsx
    │   ├── ExamplePanel.module.css
    │   ├── FieldTree.tsx
    │   ├── FieldTree.module.css
    │   ├── Operation.tsx
    │   └── Operation.module.css
    └── i18n/                           (unchanged)
        ├── format.ts
        ├── types.ts
        ├── useUiStrings.ts
        └── locales/
            ├── index.ts
            └── ar, de, en, es, fr, hi, it, ja, ko, nl, pt, ru, zh (.ts)
```

How one tag lines up after the change:

| | Location | Example |
|---|---|---|
| Schema (what authors may write) | `core/content/schema/tags/` | `callout.ts` |
| Component (what the browser shows) | `app/components/` | `callout/Callout.tsx` |
| Link between them | `app/components/component-map.ts` | `Callout` |

- **FR-001:**
  - `src/` has four folders: `core/`, `cli/`, `app/` and `types/`, as in the tree above.
  - A feature with a build part and a display part has a folder in both `core/` and `app/`, with matching names.
  - There are no `shared/` or `utils/` folders. A helper lives next to its only user, and moves to the lowest folder that uses it once shared.
  - `cli/` has one folder per command. Code shared by commands is in `cli/vite/`.
- **FR-002:**
  - Each folder imports only from the folders in the "May import from" column.
  - `app/tsconfig.json` includes only `../types`.
- **FR-003:**
  - `types/` holds types only, no code.
  - `CONDITIONAL_BADGE` is in `core/openapi/badges.ts`, and `scene.ts` is in `types/`.
- **FR-004:**
  - `createDefaultMarkdocConfig()` returns the same nodes and tags, with one file per tag in `core/content/schema/tags/`.
- **FR-005:**
  - `bin/cli.js` is only the entry point and calls `cli/<command>/index.ts`.
  - `paths.ts` finds the package root one folder deeper: `'../../../..'`.
- **FR-006:**
  - The build script clears `dist/` before compiling.

## Decisions
- **D-001:** `core/content/` and `app/components/` as folder names, because they say what the code does. Rejected: `markdoc/`, because it suggests Stripe's code. To be confirmed, see Open Issues in the [spec](./spec.md).
