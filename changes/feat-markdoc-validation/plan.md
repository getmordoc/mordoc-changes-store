# Validate Markdoc content: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `transformContent` runs `Markdoc.validate()` on each page with the same config as `Markdoc.transform()`, before transforming it.
  - The enrichment parser parses each file with its file path and runs `Markdoc.validate()` on it with the same config as the transform.
  - `runApiStages` returns these problems, and `runPipeline` reports and handles them together with the problems of the pages.
- **FR-002:**
  - Each problem is collected with the page's file path, its line, its level and its message.
  - Problems are printed as `file:line  level  message`.
- **FR-003:**
  - `mordoc build` stops after the content step when a problem has the level `error` or `critical`, with the number of problems.
- **FR-004:**
  - `reparsePage` prints the problems and does not stop.
- **FR-005:**
  - The `fence` node has the `process` attribute, as Markdoc's own `fence` node does.
  - The `fence` node builds its content from the transformed children when there are any, and from `content` otherwise, as Markdoc's own `fence` node does.
  - `CodeBlock` and `Diagram` receive that content.
  - A code block whose transformed children include a tag that renders a component gets its `content`, as written.
  - Descriptions from OpenAPI files are rendered with `process` set to `false` on their code blocks, so they stay as written.
- **FR-006:**
  - The components example site's `config/variables.yaml` has `exampleApiBaseUrl` and `exampleSdkVersion`.
  - Its `media/images.md` puts an image tag inside a link, not a Markdown image.
  - Its `guide/code.md` has a JavaScript code block that uses `exampleApiBaseUrl`, a shell code block that uses `exampleSdkVersion`, and a `{% process=false %}` code block with Markdoc syntax.
- **FR-007:**
  - The `link` node and the `link` tag allow the same children as Markdoc's own `link` node, including `tag`.
- **FR-008:**
  - The `advancedImage` tag has a `validate()` that reports, at the level `critical`, when the tag is inline: `'advancedImage' can only stand on its own line.`
- **FR-009:**
  - Every block tag has `inline: false`: callout, card, cardGrid, hero, section, accordion, accordions, column, columns, clip, videoEmbed and params.
  - `image`, `link`, `button` and `advancedImage` have an explicit `inline: undefined`.
  - `createDefaultMarkdocConfig()` throws when a tag has no `inline`.
- **FR-010:**
  - The `link` node, the `link` tag and the `button` tag have a `validate()` that reports, at the level `critical`, when one of their parents is a link or a button.
- **FR-011:**
  - `cardGrid`'s `cols` matches `1`, `2`, `3` or `4`.
- **FR-012:**
  - Validation receives the kind of text in the Markdoc config: a landing page, an article page, or a text for the API reference.
  - `hero` and `section` have a `validate()` that reports, at the level `critical` and with the tag's own name:
    - on an article page: `'hero' can only be used on a landing page. Add "layout: landing" to the page's frontmatter to use it.`
    - in a text for the API reference: `'hero' cannot be used in texts for the API reference.`

## Decisions
- **D-001:** Process and check code blocks as Markdoc does, with `{% process=false %}` to show one as written, because that is how Markdoc works. Rejected: treating every code block as raw text.
- **D-002:** Stop the build on `error` and `critical`, and only report warnings, because some warnings may come from Mordoc's tag rules being too strict. Rejected: stopping on every problem.
- **D-003:** Mordoc's versions of Markdoc's nodes allow exactly what Markdoc's own nodes allow, so a Markdown image inside a link is reported as Markdoc reports it. Rejected: allowing a Markdown image inside a link.
- **D-004:** Allow every tag inside a processed code block, as Markdoc does, because a writer who does not want it marks the code block with `{% process=false %}`. Rejected: only allowing tags that produce text.
- **D-005:** Until Mordoc can show components inside code blocks, show a code block with a component tag as written, because the page keeps working and nothing disappears silently. Showing components inside code blocks is a later change. Rejected: leaving the component out, and reporting it as a warning.
- **D-006:** Each tag checks its own place, with `inline` and its own `validate()` looking at its parents, because Markdoc passes every node's parents to its validation and new or custom tags then bring their own rules. Rejected: a link checking every tag inside it.
- **D-007:** Validate the enrichment files and not the descriptions in OpenAPI files, because enrichment files are Markdoc that authors write, and descriptions are CommonMark, often written by an API team. Rejected: validating the descriptions.
- **D-008:** Leave the texts from OpenAPI files as they were, because they belong to the API, not to the documentation, and are not validated. Rejected: processing their code blocks as Markdoc.
- **D-009:** Stop the build when a hero or a section is used outside a landing page, with a message that says how to fix it, because the page cannot show it. Rejected: leaving the tag out silently, and a separate set of tags per kind of page, which only reports an undefined tag.
