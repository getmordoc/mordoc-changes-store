# Modernize Mordoc's default look and feel: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, in the CSS modules under `src/app`, with one class added in `Sidenav.tsx`.
- **FR-001:**
  - `Sidenav.tsx` marks a depth-0 group without a path as a category.
  - A category's title is 14px, weight 600, uppercase, in `--sidenav-group-label-fg`, which defaults to the main text color.
  - A category that is not the first menu item has a 1px top border in `--color-border`, with 16px space above and below it.
- **FR-002:**
  - `--sidenav-font-weight` is 400 and sidenav rows are at least 32px high.
  - `--sidenav-active-bg` is transparent.
- **FR-003:**
  - An `h2` directly in the prose has a 1px top border in `--color-border` and space above it, except as the first child.
- **FR-004:**
  - Page title 32px; intro 20px; `h2` 24px, `h3` 20px, `h4` 18px, `h5` 16px, `h6` 15px.
  - `--color-content-fg` is `#404040` in light mode.
  - The "On this page" title is 13px, weight 500, uppercase; its links use `--color-content-fg`.
- **FR-005:**
  - `--cb-code-bg` and `--cb-fg` in `CodeBlock.module.css` set the code's background and text; `--cb-bg` sets the title bar.
  - Light and dark mode share the dark values; dark mode adds a border in `--cb-border`.
  - The Prism token colors use the current dark palette in both modes.
- **FR-006:**
  - The `--accent` value and all existing token names stay.

## Decisions
- **D-001:** Keep Inter, because it looks the same on every computer and ships with Mordoc. Rejected: the computer's own font, as Stripe uses.
- **D-002:** A neutral near-black for code blocks, because it suits the red accent. Rejected: Stripe's navy, which is part of Stripe's brand.
- **D-003:** Categories keep opening and closing, because sites rely on it for long sidebars. Rejected: always-open categories, as Stripe has.
