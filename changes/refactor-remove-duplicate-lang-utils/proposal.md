# Remove the duplicate language helpers

## Description
As a Mordoc contributor, I want the language helpers to exist in one place, so that a fix to them applies everywhere and I don't have to keep two copies the same.

## Why
- The website and the build each have their own copy of the language helpers. The build uses only one of them, to work out a page's language, which it already knows.

## What
- One copy of the language helpers, used by the website.
- The build takes each page's language from what it already knows about the page.
