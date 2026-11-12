# Validate Markdoc content

## Description
As a docs author, I want Mordoc to validate all Markdoc content in my pages and report each mistake with the file and line number, so that mistakes are caught and not silently ignored.

## Why
- Mordoc does not validate content today, so unknown tags, invalid options, undefined variables and wrongly nested content are silently ignored.

## What
- Mordoc validates all Markdoc content, including code blocks, as Markdoc intends.
- Code blocks that show Markdoc syntax, such as the examples in the Mordoc documentation, fail validation. The right approach is to mark those code blocks with `{% process=false %}`, so that Markdoc shows them as written, and not to turn validation off.
- Variables in code blocks are filled in with their value from the site's settings, as Markdoc intends, such as an API address or a version number in a code sample.
- Mordoc allows exactly what Markdoc allows. For example, a tag such as the image tag may be placed inside a link, while a Markdown image inside a link is reported as a warning, as Markdoc does.
