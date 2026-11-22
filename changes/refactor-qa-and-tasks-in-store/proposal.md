# Keep every document of a change in one folder

## Description
As a Mordoc contributor, I want all documents of a change in one folder in the store, so that I can follow a change in one place.

## Why
- A change's `qa.md` and `tasks.md` are spread over Mordoc's `changes/` folder and the store, in two different layouts, and documents link to each other with links that break when folders move.
- Every change is easy to follow, and the code repositories hold only code.

## Steps to Reproduce
None

## What
- Every change in the store has its `qa.md` and `tasks.md` in a subfolder named after the repository where it was built.
- Mordoc no longer has a `changes/` folder.
- Changes refer to each other by folder name, without links.
- The store's README describes this layout.
