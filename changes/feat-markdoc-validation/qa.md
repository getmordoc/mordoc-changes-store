# Validate Markdoc content: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Build test sites with Mordoc from this change's branch: the components example site, a copy of it with test pages that contain each kind of mistake, a copy of the Mordoc documentation, and a copy of the API demo site. Check the build output, the built pages in Chrome, and the development server.
- Pages without variables or tags in code blocks must render as they do with `main`.
- The API demo's operation pages must render the texts from its OpenAPI files as they do with `main`.
- Setup: Node.js 24. In the Mordoc repository `npm run build`; in a site folder `node <mordoc>/bin/cli.js build` or `node <mordoc>/bin/cli.js dev`.

## Test Coverage
- **AC-001:** Build a test page with an unknown tag, one with an invalid option value and one with an undefined variable: each build stops, and the output names the file, the line and the problem.
- **AC-002:** Build a test page with only a warning, such as text nested where it is not allowed: the build finishes, and the warning shows with its file and line.
- **AC-003:** With the development server running, save a page with an unknown tag: the problem shows in the terminal, the server keeps running, and fixing the page clears it.
- **AC-004:** Open a page with a code block that uses a variable the site defines: the code block shows the value; the copy button copies the code with the value.
- **AC-005:** Open a page with a code block marked `{% process=false %}` that contains Markdoc syntax: it shows exactly what was written, and the build reports nothing for it.
- **AC-006:** Build a page with an undefined variable inside a code block: the build stops and reports it.
- **AC-007:** Build the components example site: no problems are reported.
- **AC-008:** Open the components example site's code page: the JavaScript and shell code blocks show the site's variable values, and the Markdoc syntax code block shows as written.
- **AC-009:** Build a page with an image tag inside a link: no problem is reported; clicking the image opens the link.
- **AC-010:** Build a page with a Markdown image inside a link: the build finishes and reports a warning with its file and line.
- **AC-011:** Build a page with an advanced image inside a sentence, and one inside a link: each build stops and reports the file, the line, and that an advanced image can only stand on its own line.
- **AC-012:** Open a page with a code block that contains a callout tag and is not marked to be shown as written: it shows exactly what was written, and the console has no errors.
- **AC-013:** Build a page with a callout inside a sentence, and one with a video inside a link: each build stops and reports the file and line.
- **AC-014:** Build a page with a link inside a link, and one with a button inside a link: each build stops and reports that one click can only go to one place.
- **AC-015:** Generate one page per tag and place (own line, sentence, Markdown link, link tag, button, and inside callout, accordion, column, card and section), as article pages and, for hero, section and the section place, as landing pages. Build them without stopping, open each in Chrome and record browser errors. Compare with validation: every page with a browser error, and every page that cannot be built, is stopped by validation.
- **AC-016:** In the copy of the API demo site, add an unknown tag to an enrichment file and build: the build stops, and the output names the file, the line and the problem. With the development server running, save the same mistake: it is reported and the server keeps running.
- **AC-017:** Build a page without `layout: landing` that has a hero, and one that has a section: each build stops and reports the file, the line, and `Undefined tag`. Add `layout: landing`: the build finishes.
- **AC-018:** In the copy of the API demo site, add a hero to an enrichment file and build: the build stops and reports the file, the line, and `Undefined tag`.
