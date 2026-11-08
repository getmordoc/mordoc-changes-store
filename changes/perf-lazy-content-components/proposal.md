# Load content components per page

## Description
As a site reader, I want each page to load only the components it uses, so that adding more components to Mordoc doesn't make every page heavier.

## Why
- Every page loads every component: 612 KB, or 193 KB compressed, on a 134-page site measured in November 2026. This grows with each new component.

## What
- Each page loads only the components it uses.
- Heavy, rarely used components, such as diagrams, video and API pages, are the first candidates.
