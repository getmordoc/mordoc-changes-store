# Write property access and strings the usual way: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-001, FR-002, FR-003:**
  - One commit with only the fixes of Biome's `useLiteralKeys`, `useTemplate` and `noUselessSwitchCase`, made with `biome lint --write --unsafe` for those rules, and formatted.
  - `.git-blame-ignore-revs` holds that commit's hash.
- **FR-004:**
  - `biome.jsonc` sets `useLiteralKeys`, `useTemplate` and `noUselessSwitchCase` to `warn`; `npm run check` fails on warnings.
- **NFR-001:**
  - `examples/components`, `mordoc-docs` and `mordoc-api-demo` build the same `dist/` before and after.

## Decisions
- **D-001:** Dot notation and template literals, because they are the usual JavaScript conventions, as in ESLint's `dot-notation` and `prefer-template` and the Airbnb style guide. Rejected: brackets for data read from YAML or JSON, which TypeScript's `noPropertyAccessFromIndexSignature` would ask for, but Mordoc doesn't use it.
- **D-002:** The rules as warnings, because `npm run check` fails on warnings, as on the other rules. Rejected: leaving them as tips.
