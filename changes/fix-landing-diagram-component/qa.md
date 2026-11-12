# Diagrams on landing pages: QA Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**Technical plan:** [plan.md](./plan.md)

## Test Strategy
- Build the components example site from this change's branch, and open its landing page and diagrams page in Chrome, in light and dark theme. Every other component on the landing page must look as it does on `main`.
- Setup: Node.js 24. In the Mordoc repository `npm run build`; in `examples/components` `npm run build` and `python3 -m http.server 4173 -d dist`.

## Test Coverage
- **AC-001:** On `main`, add a diagram to the components example site's landing page and build: the build stops. On this change's branch, build the site: the build succeeds.
- **AC-002:** Open the landing page: the diagram looks the same as on the diagrams page, in light and dark theme, and the browser console has no errors.
- **AC-003:** Open the components example site's landing page: it shows the diagram.
