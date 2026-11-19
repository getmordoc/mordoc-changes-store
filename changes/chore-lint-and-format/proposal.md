# Lint and format the code

## Description
As a Mordoc contributor, I want the code checked for common mistakes and formatted the same way everywhere, so that reviews are about what the code does and not about its style.

## Why
- Nothing checks the code for common mistakes, such as unused code or wrong use of React hooks.
- Formatting depends on who wrote the code, so changes mix real edits with style differences.
- Mordoc uses TypeScript 7, which the usual linting setup doesn't support yet.
- Mistakes are caught before they reach users, and reviews take less time because they are only about real changes.

## What
- One tool that checks the code for common mistakes and formats it, with a command to check and a command to fix.
- All existing code formatted once, in a commit of its own.
- The check runs with the other tests, locally and for every pull request.
