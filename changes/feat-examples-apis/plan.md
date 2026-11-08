# APIs example site: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)
**Tasks:** [tasks/](./tasks/)

## Approach
- Directory structure:
```
examples/apis/
├── README.md
├── package.json
├── api/
│   ├── specs/          pets.yaml, orders.yaml
│   ├── examples/       pets/getPet/
│   └── enrichment/     pets/operations/, pets/schemas/
├── config/
│   ├── site.json
│   ├── api.yaml
│   └── navigation/     sidenav.yaml
└── content/en/
    └── index.md
```
- The `api/` files and `reference.yaml` move from `examples/components/`.
- **FR-001:**
  - `README.md` and `package.json` as in `examples/components/`.
  - `config/site.json` with the required fields.
- **FR-002:**
  - `config/api.yaml` lists `pets` and `orders`, and `orders` has the `routePrefix` `/api/store`.
  - The specs have path, query, header and cookie parameters, request bodies, responses, `$ref` schemas, `oneOf`, a recursive schema, a deprecated operation and a webhook.
- **FR-003:**
  - `createPet` has named examples in the spec.
  - `getPet` has a file in `api/examples/pets/getPet/`.
  - `createOrder` has no example.
- **FR-004:**
  - `createPet.md` has text, `{% params %}` and `{% params in="response" status="201" %}`.
  - `listPets.md` has `{% params mode="replace" %}`.
  - Fields have a `conditional` badge and a free text badge.
  - `schemas/Error.md` adds text to a schema.
- **FR-005:**
  - `sidenav.yaml` is the current `reference.yaml`, with `operation:` links with and without a label.

## Decisions
- None
