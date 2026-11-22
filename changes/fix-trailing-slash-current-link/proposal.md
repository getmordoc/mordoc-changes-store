# Mark only the current page in the sidebar after opening an address that ends in a slash

## Description
As a reader, I want the sidebar to mark only the page I am on, so that I always see where I am, also on hosts that add a slash to the end of each address.

## Why
- Some hosts, such as GitHub Pages and Python's built-in server, open each page at an address that ends in a slash, like `/getting-started/run-locally/`.
- After such an address, the sidebar keeps the first page marked as current in red, next to every page the reader opens after it, until they reload.
- A sidebar that marks two pages confuses readers about where they are, and screen readers announce both as the current page.
- An address with capital letters, such as `/Media`, shows the right page, but the sidebar doesn't mark it.
- Readers always see where they are, on every host.

## Steps to Reproduce
1. Build the Mordoc documentation, and serve the built site with `python3 -m http.server`.
2. Open a page at an address that ends in a slash, such as `/getting-started/run-locally/`.
3. Open another page from the sidebar.
- **What happens:** The sidebar marks both pages as current, and keeps the first page marked until the reader reloads.
- **What should happen:** The sidebar marks only the page the reader is on.

## What
- Only the current page is marked in the sidebar, whether the address ends in a slash or not, and whatever letters are capitals.
- The sidebar and breadcrumb show the current page for an address in any letter case.
