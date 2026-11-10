# Markdown images cause a browser error

## Description
As a site reader, I want pages with images to load with no errors, so that the page works as intended.

## Why
- Every page with a Markdown image logs a browser error, although the image still shows. To reproduce:
  1. Build and serve the components example site, as its README says under "Open the built site".
  2. Open http://localhost:4173/media/images/ and the browser console: it shows "Minified React error #418".
- What happens:
  - Markdoc puts a Markdown image inside a paragraph, also when the image is on its own line.
  - Mordoc shows the image as a figure with a caption, so the built page has a figure inside a paragraph: `<p><figure>…</figure></p>`.
  - HTML doesn't allow a figure inside a paragraph. While reading the page, the browser closes the paragraph before the figure, so the figure ends up outside it.
  - React then takes over the page in the browser. It expects the figure inside the paragraph, finds it outside, and reports the mismatch as error #418.
- An image on its own line:
  ```markdown
  ![A map of the Orbit system](/images/orbit-map.svg "The Orbit system")
  ```
  The built page has:
  ```html
  <p><figure><img src="/images/orbit-map.svg" alt="A map of the Orbit system"><figcaption>The Orbit system</figcaption></figure></p>
  ```
  The browser turns it into:
  ```html
  <p></p>
  <figure><img src="/images/orbit-map.svg" alt="A map of the Orbit system"><figcaption>The Orbit system</figcaption></figure>
  <p></p>
  ```
- An image inside a sentence has the same problem:
  ```markdown
  Click the ![settings icon](/icons/gear.svg) icon to open settings.
  ```
  The built page has:
  ```html
  <p>Click the <figure><img src="/icons/gear.svg" alt="settings icon"></figure> icon to open settings.</p>
  ```
  The browser turns it into:
  ```html
  <p>Click the </p>
  <figure><img src="/icons/gear.svg" alt="settings icon"></figure>
  icon to open settings.
  <p></p>
  ```
- This must be fixed before the [browser tests for the components example site](../test-e2e-components/proposal.md), which check that pages load with no errors.

## What
- Pages with images load with no errors.
- Every image, written in Markdown or with the image tag, shows as a plain image with rounded corners and a shadow: on its own line, inside a sentence and inside a link. Its title shows when hovering over it.
- A new advanced image tag has everything the image tag has today: a visible caption below the image, a hover effect, and opening larger when clicked. An advanced image stands on its own line.
- The Mordoc documentation and the components example site describe images and advanced images as they work.
