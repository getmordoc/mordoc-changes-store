# Mordoc changes store

How Mordoc is built, spec-first: a proposal, specification and plan for every change.

Mordoc is built with spec-driven development. Before any code is written, each change is described here in plain language, using the templates in [`changes/_templates/`](changes/_templates), and reviewed. The pull request in the code repository shows how the change was tested.

## How a change is documented

Every change has its own folder in [`changes/`](changes), named after its type and a short name, such as `feat-markdoc-validation` or `fix-accessibility`. The type is one of `feat`, `fix`, `refactor`, `perf`, `test`, `docs` or `chore`.

| Document | What it says |
|---|---|
| `proposal.md` | The user story, why the change is needed and what we would like to have. |
| `spec.md` | The requirements, acceptance criteria, boundaries and constraints. |
| `plan.md` | What must exist to meet each requirement, in the order to build it, and the technical decisions. |

Each code repository where the change is built has a folder with the same name in its own `changes/`, with `qa.md` (how the change is verified, decided before it is built) and `tasks.md` (the tasks to build it).

## Documentation

Read the Mordoc documentation at [mordoc.dev](https://mordoc.dev).

## Get started

Open any folder in [`changes/`](changes) and read its documents in the order above.

To start a new change, copy the templates in [`changes/_templates/`](changes/_templates).

## License

The changes store is released under the [MIT License](LICENSE). The authors are listed in [AUTHORS](AUTHORS).
