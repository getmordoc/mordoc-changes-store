# Write property access and strings the usual way

## Description
As a Mordoc contributor, I want the code to follow the usual JavaScript conventions for reading properties and building strings, so that it reads the same everywhere and the code check keeps it that way.

## Why
- About 200 places read a property with brackets and a fixed name, such as `obj['languages']`, where JavaScript code usually writes `obj.languages`.
- A few places join strings with `+` instead of a template literal, and one `switch` has a case that does nothing.
- The code check only gives these as tips, which nobody sees, so the style keeps drifting apart.
- One style that the code check enforces, so reviews don't have to discuss it.

## What
- All of these places written the usual way.
- The code check failing on them from now on.
