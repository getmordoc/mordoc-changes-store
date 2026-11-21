# Mark only the current page in the sidebar after opening an address that ends in a slash

## Description
As a reader, I want the sidebar to mark only the page I am on, so that I always see where I am, also on hosts that add a slash to the end of each address.

## Why
- Some hosts, such as GitHub Pages and Python's built-in server, open each page at an address that ends in a slash, like `/getting-started/run-locally/`.
- After such an address, the sidebar keeps the first page marked as current in red, next to every page the reader opens after it, until they reload.
- A sidebar that marks two pages confuses readers about where they are, and screen readers announce both as the current page.

## What
- Only the current page is marked in the sidebar and the other navigation, whether the address ends in a slash or not.
