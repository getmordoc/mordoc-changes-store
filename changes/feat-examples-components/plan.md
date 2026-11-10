# Components example site: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- Directory structure:
```
examples/components/
├── README.md
├── package.json
├── config/
│   ├── site.json
│   ├── variables.yaml
│   └── navigation/     topnav.yaml, guide.yaml, media.yaml,
│                       headernav.yaml, footer.yaml
├── content/en/
│   ├── index.md
│   ├── guide/          pages from the table below
│   └── media/          pages from the table below
└── public/             image, video and a downloadable file
```
- Pages:

| Page | Covers |
|---|---|
| `index.md` | `hero`, `section`, `button`, `cardGrid`, `card` |
| `guide/index.md`, `media/index.md` | Overview page for each top navigation area |
| `guide/callouts.md` | `callout` |
| `guide/cards.md` | `card`, `cardGrid` |
| `guide/buttons.md` | `button` |
| `guide/text.md` | `heading` node, `{% table %}` |
| `guide/links.md` | `link` node and tag, a link to an unknown route |
| `media/images.md` | `image` node and tag, on their own line, inside a sentence and inside a link |
| `media/advanced-images.md` | `advancedImage` tag |
| `media/video.md` | `clip`, `videoEmbed` |
| `guide/accordions.md` | `accordion`, `accordions` |
| `guide/columns.md` | `column`, `columns` |
| `guide/code.md` | `fence` node |
| `media/diagrams.md` | `sequence-diagram` fence |

- **FR-001:**
  - `README.md` with the steps: `npm install` and `npm run build` in the repo root, then `npm run build` or `npm run dev` in the site.
  - `package.json` with `dev` and `build` scripts that run `node ../../bin/cli.js`, and no dependencies.
  - `config/site.json` with the required fields.
- **FR-002:**
  - Each page uses every attribute and `matches` value of its tags, as defined in `createDefaultMarkdocConfig()`.
  - `media/diagrams.md` uses every syntax option in `src/diagrams/sequence-diagram/`.
- **FR-003:**
  - `index.md` has `layout: landing`.
  - Each article page has headings.
  - `public/` has one image, one video and one downloadable file.
- **FR-004:**
  - `topnav.yaml` has two areas: Guide at `/guide` and Media at `/media`.
  - `headernav.yaml` has every `variant`.
  - `footer.yaml` has all three columns.
  - `variables.yaml` is used in `guide/links.md`, `media/images.md` and `media/advanced-images.md`.

## Decisions
- **D-001:** Run the repo's CLI directly, because it always uses the local code. Rejected: installing Mordoc in the site.
