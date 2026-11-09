# Figure tag

## Description
As a docs author, I want to add a figure with a visible caption, so that I can explain an image, such as a screenshot or a diagram, right below it.

## Why
- Mordoc shows every image as a figure today, which causes a browser error when the image is inside a paragraph, see [fix-markdown-image-error](../fix-markdown-image-error/proposal.md). Images become plain images, so a separate way to add a caption is needed.
- A figure with a caption is common in guides, tutorials and architecture documents.

## What
- A `{% figure %}` tag that shows an image with a visible caption below it, and opens larger when clicked.
- A figure stands on its own line. Mordoc reports a figure inside a sentence, in the author's terms.
