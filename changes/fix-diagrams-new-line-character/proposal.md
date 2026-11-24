# Break the actor name onto a new line in sequence diagrams

## Description
As a documentation author, I want `\n` in an actor name of a sequence diagram to start a new line, so that I can keep long actor names short and readable, like I can in a message.

## Why
- A message in a sequence diagram breaks onto a new line at `\n`, but an actor name does not.
- An author who writes `actor browser as "Merchant client \nBrowser"` sees `Merchant client \nBrowser` in the diagram, with the characters `\n` shown as text.
- Long actor names cannot be shortened, so they crowd the diagram or overlap the name of the next actor.
- Authors write a new line the same way in the actor names and in the messages of a diagram.

## Steps to Reproduce
1. Add a sequence diagram with the line `actor browser as "Merchant client \nBrowser"`, and a message that uses `browser`.
2. Build or run the documentation, and open the page.
- **What happens:** The actor name shows `Merchant client \nBrowser` on one line.
- **What should happen:** The actor name shows `Merchant client` on the first line and `Browser` on the second line.

## What
- `\n` in an actor name starts a new line, like it does in a message.
