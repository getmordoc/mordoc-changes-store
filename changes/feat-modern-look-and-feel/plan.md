# Modernize Mordoc's default look and feel: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`, in the CSS modules under `src/app`, with one class added in `Sidenav.tsx`, and in `mordoc-docs`, in its customization pages and its own hero color for its illustration.
- **FR-001:**
  - `Sidenav.tsx` marks each depth-0 group as a category.
  - A category's title is 14px, weight 600, uppercase, in `--sidenav-fg`.
  - A category that is not the first menu item has a 1px top border in `--color-border`, with 12px space above and below it.
  - In a menu with categories, a top-level page has the same left padding as a page inside a category.
- **FR-002:**
  - `--sidenav-font-weight` is 400 and sidenav rows are at least 32px high.
  - `--sidenav-active-bg` is transparent.
- **FR-003:**
  - An `h2` directly in the prose has a 1px top border in `--color-border` and space above it, except as the first child.
- **FR-004:**
  - Page title 32px; intro 20px; `h2` 24px, `h3` 20px, `h4` 18px, `h5` 16px, `h6` 15px.
  - `--color-content-fg` is `#404040` in light mode.
  - The "On this page" title is 13px, weight 500, uppercase; its links keep `--color-fg-muted`.
- **FR-005:**
  - `--cb-code-bg` and `--cb-fg` in `CodeBlock.module.css` set the code's background and text; `--cb-bg` sets the title bar.
  - Light mode: title bar `#eeeeee`, code `#fafafa`; dark mode: title bar `#121212`, code `#1e1e1e`; both with a border in `--cb-border`.
  - The Prism token colors come from the `--cb-token-*` settings, with a light and a dark set.
- **FR-006:**
  - The `--accent` value and all existing token names stay.
  - `--cb-token-comment`, `-punctuation`, `-constant`, `-string`, `-operator`, `-keyword`, `-function` and `-variable` in `CodeBlock.module.css` set the highlight colors.
  - `--sidenav-category-fg` and `--sidenav-category-font-weight` in `Sidenav.module.css`.
  - `--heading-divider-color` in `Typography.module.css`.
  - The `mordoc-docs` customization pages, in English and German, list the new settings and changed defaults.
- **FR-007:**
  - `--header-area-bg` is `#fafafa` in light mode and `#272727` in dark mode.
  - `--hero-bg` is `#f5f5f5` in light mode and `#1e1e1e` in dark mode; `--hero-desc-color` is `#616161` in light mode.
  - `mordoc-docs` sets only its own light hero color, `#f5f4f2`, in `config/styles/hero.css`.
  - `--search-bar-bg` is `#ffffff` in light mode and `#121212` in dark mode, with `--search-bar-border` `#3a3a3a` in dark mode.

- **FR-008:**
  - `--skeleton-bg` and `--skeleton-highlight` in `Skeleton.module.css`: `#eeeeee` and `#fafafa` in light mode, `#272727` and `#383838` in dark mode.
  - The shimmer gradient runs from `--skeleton-bg` to `--skeleton-highlight` and back.
- **FR-009:**
  - `--font-mono` is Menlo, Consolas, `monospace`, the same list as Stripe.
  - Code blocks are 13px with a 19px line height.
  - The search shortcut key uses `--font-mono`.

## Decisions
- **D-001:** Keep Inter, because it looks the same on every computer and ships with Mordoc. Rejected: the computer's own font, as Stripe uses.
- **D-002:** Light code blocks under a darker grey title bar in light mode, and near-black in dark mode, because a dark block is too heavy on a light page. Rejected: dark code blocks in both modes, as Stripe has.
- **D-003:** Categories keep opening and closing, because sites rely on it for long sidebars. Rejected: always-open categories, as Stripe has.
- **D-004:** Swap a color for its nearest Material Design color only when the CIEDE2000 difference is at most 3, because up to that the change is barely visible. Rejected: Material colors for every value, which would visibly change the callouts, diagrams and code highlighting.
- **D-005:** The Mordoc documentation gives its hero a light grey with a hint of warmth for its illustration, because a site's own colors need not be Material colors. Rejected: a warm Mordoc default, which would not suit every site's images.
- **D-006:** Use each system's own code font, because Mordoc embeds nothing from other companies. Rejected: shipping JetBrains Mono, which would look the same everywhere.
