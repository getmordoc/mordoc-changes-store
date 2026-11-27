# One report for the problems in the content

## Description
As a documentation author, I want each problem in my content listed once, also when another error stops the build, so that I can fix them all in one go.

## Why
- A problem in a page that is also shown in other languages is listed once for each language.
- When an OpenAPI file can't be loaded, the build stops without listing the problems in the pages.
- The checks for names and paths that come next need a place for their problems, also for problems without a line, such as a file name that isn't allowed.

## Steps to Reproduce
1. Make a site with the languages `en`, `de` and `fr`, and put `{% banner %}Text{% /banner %}` in `content/en/page.md`.
2. Run `mordoc build`.
- **What happens:** "Undefined tag: 'banner'" is listed three times.
- **What should happen:** It's listed once.
3. Add an API to `config/api.yaml` whose OpenAPI file doesn't exist, and run `mordoc build` again.
- **What happens:** Only the missing OpenAPI file is reported.
- **What should happen:** The problem in the page is listed too.

## What
- Mordoc collects the problems of the pages and the texts for the API reference in one list, each problem once.
- The list is shown also when another error stops the build.
- The preview shows each problem once, also after a file is saved.
- Other checks can add their problems to the same list, with or without a line.
