# Write property access and strings the usual way: QA Plan

**Change:** `refactor-dot-notation-and-templates`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Before the first task, build `examples/components`, `../mordoc-docs` and `../mordoc-api-demo` with `main`, and keep their `dist/` and build output as the baseline.
- After each task: `npm run build` and `npm test`.

## Test Coverage
- **AC-001:** `npx biome lint` reports no `useLiteralKeys`, `useTemplate` or `noUselessSwitchCase`; the brackets left in the code hold a variable or a name that isn't a valid identifier.
- **AC-002:** With a bracket property, a `+` string and a useless `switch` case added to a temporary file, `npm run check` fails and shows each of them; without the file it passes.
- **NFR-001:** The three sites build the same `dist/` and the same build messages as the baseline.
