# Lowercase page addresses from file names

## Description
As a documentation author, I want Mordoc to make clean page addresses from my file names and check the paths I write, so that links work on every host.

## Why
- File names can contain any character, and some give pages that can't be opened.
- Capital letters in an address work locally, but give "page not found" on many hosts.
- A wrong path in the navigation or in a page gives a broken link, without any warning.
- Readers get fewer broken links, because authors see mistakes when they build.

## Steps to Reproduce
None

## What
- File and folder names use letters, digits, hyphens and underscores.
- Page addresses are always lowercase.
- Authors write paths in any letter case, in the navigation and in links inside pages, and the built site uses the page's address.
- The build stops with a clear error for a name that isn't allowed, two pages with the same address, or a path without a page.
- The addresses and errors are the same while previewing the site locally and when building it, also after saving a file; the preview keeps running while the author fixes an error.
