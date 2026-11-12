# Validate Markdoc content: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - A `ContentValidator` runs `Markdoc.validate()` on a text and keeps the results; `runPipeline` and `reparsePage` each create a new one for every run and pass it to the page transformer and the enrichment parser.
  - `transformContent` validates each page with the same config as `Markdoc.transform()`, before transforming it.
  - The enrichment parser parses each file with its file path and validates it with the same config as the transform: the article config, with the `badge` attribute declared on headings.
- **FR-002:**
  - Each problem is collected with the page's file path, its line, its level and its message.
  - Problems are printed as `file:line  level  message`.
- **FR-003:**
  - `mordoc build` stops after the content and API steps when a problem has the level `error` or `critical`, with the number of problems.
- **FR-004:**
  - `reparsePage` prints the problems and does not stop.
- **FR-005:**
  - The `fence` node has the `process` attribute, as Markdoc's own `fence` node does.
  - The `fence` node builds its content from the transformed children when there are any, and from `content` otherwise, as Markdoc's own `fence` node does.
  - `CodeBlock` and `Diagram` receive that content.
  - A code block whose transformed children include a tag that renders a component gets its `content`, as written.
  - The `fence` node shows its `content` as written when its `process` attribute is `false`.
  - Descriptions from OpenAPI files are rendered with a config whose `fence` has `process` set to `false` by default.
- **FR-006:**
  - The components example site's `config/variables.yaml` has `exampleApiBaseUrl` and `exampleSdkVersion`.
  - Its `media/images.md` puts an image tag inside a link, not a Markdown image.
  - Its `guide/code.md` has a JavaScript code block that uses `exampleApiBaseUrl`, a shell code block that uses `exampleSdkVersion`, and a `{% process=false %}` code block with Markdoc syntax.
- **FR-007:**
  - The `link` node and the `link` tag allow the same children as Markdoc's own `link` node, including `tag`.
- **FR-008:**
  - The `advancedImage` tag's `inline: false` is reported by validation at the level `critical`.
- **FR-009:**
  - Every block tag has `inline: false`: callout, card, cardGrid, hero, section, accordion, accordions, column, columns, clip, videoEmbed, advancedImage and params.
  - `image`, `link` and `button` have an explicit `inline: undefined`.
  - `createDefaultMarkdocConfig()` throws when a tag has no `inline`.
- **FR-010:**
  - The `link` node, the `link` tag and the `button` tag have a `validate()` that reports, at the level `critical`, when one of their parents is a link or a button.
- **FR-011:**
  - `cardGrid`'s `cols` matches `1` up to `CARD_GRID_MAX_COLUMNS` (4), defined next to the `cardGrid` schema; `CardGrid` uses the value as it is.
- **FR-012:**
  - There are two sets of tags: the article tags, and the landing tags, which are the article tags plus `hero` and `section`.
  - A page with `layout: landing` is validated and transformed with the landing tags; every other page and every text for the API reference with the article tags.

## Decisions
- **D-001:** Process and check code blocks as Markdoc does, with `{% process=false %}` to show one as written, because that is how Markdoc works. Rejected: treating every code block as raw text.
- **D-002:** Stop the build on `error` and `critical`, and only report warnings, because some warnings may come from Mordoc's tag rules being too strict. Rejected: stopping on every problem.
- **D-003:** Mordoc's versions of Markdoc's nodes allow exactly what Markdoc's own nodes allow, so a Markdown image inside a link is reported as Markdoc reports it. Rejected: allowing a Markdown image inside a link.
- **D-004:** Allow every tag inside a processed code block, as Markdoc does, because a writer who does not want it marks the code block with `{% process=false %}`. Rejected: only allowing tags that produce text.
- **D-005:** Until Mordoc can show components inside code blocks, show a code block with a component tag as written, because the page keeps working and nothing disappears silently. Showing components inside code blocks is a later change. Rejected: leaving the component out, and reporting it as a warning.
- **D-006:** Each tag checks its own place, with `inline` and its own `validate()` looking at its parents, because Markdoc passes every node's parents to its validation and new or custom tags then bring their own rules. Rejected: a link checking every tag inside it.
- **D-007:** Validate the enrichment files and not the descriptions in OpenAPI files, because enrichment files are Markdoc that authors write, and descriptions are CommonMark, often written by an API team. Rejected: validating the descriptions.
- **D-008:** Leave the texts from OpenAPI files as they were, because they belong to the API, not to the documentation, and are not validated. Rejected: processing their code blocks as Markdoc.
- **D-009:** Give each kind of page its own set of tags, the landing tags being the article tags plus `hero` and `section`, as the page components are, because the kind of page then decides which tags exist and Markdoc reports any other tag as undefined. Rejected: a check inside `hero` and `section` for the kind of page, and leaving the tag out silently.
