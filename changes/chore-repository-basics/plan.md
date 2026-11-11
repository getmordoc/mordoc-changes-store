# Repository basics: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `LICENSE` in every repository has this text, MIT with the new copyright line:

```text
MIT License

Copyright (c) 2026 The Mordoc Authors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

- **FR-002:**
  - `AUTHORS` in `mordoc`, `create-mordoc-app`, `mordoc-docs`, `mordoc-api-demo` and `mordoc-changes-store` has this text:

```text
# This is the list of the Mordoc authors for copyright purposes.

Shiva Varanasi
Siebe Brouwer
```

- **FR-003:**
  - `package.json` in `mordoc`, `create-mordoc-app` and `mordoc-api-demo` has `"author": "The Mordoc Authors"`.
- **FR-004:**
  - The GitHub descriptions are:
    - `mordoc`: "A documentation framework that turns Markdoc content into fast, static documentation websites."
    - `mordoc-docs`: "The documentation website for Mordoc, built with Mordoc."
    - `create-mordoc-app`: "Create a new Mordoc documentation website with one command."
    - `mordoc-changes-store`: "How Mordoc is built, spec-first: a proposal, specification, plan and QA plan for every change."
    - `mordoc-api-demo`: "A demo website for Mordoc's API reference mode, published at api-demo.mordoc.dev."
  - The GitHub topics are:
    - `mordoc`: `documentation`, `static-site-generator`, `markdoc`, `docs-as-code`, `react`, `vite`, `typescript`
    - `mordoc-docs`: `documentation`, `mordoc`, `markdoc`, `docs-as-code`
    - `create-mordoc-app`: `cli`, `scaffolding`, `documentation`, `mordoc`
    - `mordoc-api-demo`: `openapi`, `api-reference`, `documentation`, `mordoc`
    - `mordoc-changes-store`: `spec-driven-development`, `specifications`, `markdown`, `mordoc`
  - The GitHub website field of `mordoc-docs` is `https://mordoc.dev`, and of `mordoc-api-demo` is `https://api-demo.mordoc.dev`.
- **FR-005:**
  - Every `README.md` starts with the repository's name as the title and the GitHub description as its first line, and has a link to `https://mordoc.dev`.
  - `mordoc-docs` gets a `README.md`: the site is the documentation for Mordoc, built with Mordoc.
  - The README files of `mordoc`, `create-mordoc-app`, `mordoc-api-demo` and `mordoc-changes-store` follow the same structure.

## Decisions
- **D-001:** Name "The Mordoc Authors" in the license and list the names in an AUTHORS file, because it reads as one project and stays correct when others contribute, as in Go and Chromium. Rejected: naming each person in the license.
- **D-002:** Keep the AUTHORS file to the list of names, because each author keeping the copyright in their own contributions is already the law. Rejected: stating it in the file.
- **D-003:** Use the standard MIT text, with the title line "MIT License", because it is the form GitHub and other tools recognize. Rejected: keeping the current text without a title.
- **D-004:** License the documentation, the API demo and the changes store under MIT, because their examples and templates are copied into other repositories like code, and all repositories then share one license. Rejected: CC BY 4.0.
