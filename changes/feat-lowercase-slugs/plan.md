# Lowercase page paths from file names: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-007:**
  - `BuildReport` in `src/core/build-report.ts` collects, prints and stops on the problems of one run, each with a level, a message, and a file and line when there are any. It knows nothing about Markdoc.
  - `ContentValidator` in `src/core/content/content-validator.ts` validates Markdoc texts, and `RouteValidator` in `src/core/content/route-validator.ts` validates names and routes. Both add their problems to the `BuildReport`.
  - The report's heading says that Mordoc, not Markdoc, found the problems.
  - The report is also printed when another error stops the run.
  - The pipeline creates the report and the validators before it loads the content, and passes a validator to each step that needs one.
  - A fallback page isn't validated again, so each problem is reported once.
- **FR-001:**
  - `validateName(name)` in `route-validator.ts` checks `/^[A-Za-z0-9][A-Za-z0-9_-]*$/` and gives `{ valid: true }`, or `{ valid: false, error }` with the characters that aren't allowed.
  - `listMarkdocFiles` in `src/core/list-markdoc-files.ts` lists the Markdoc files, with `.md` in any letter case, for pages and for enrichment: it reads only files and folders, not symbolic links, and skips a file when its name or one of its folders starts with a dot. The list is sorted, so every system reports the same.
  - `RouteValidator` checks each folder and file name of a page with `validateName` and reports every problem, and `loadContent` leaves a page with a problem out.
  - A file that ends in `.md` in another letter case is reported, with the new name when that is allowed.
  - A dot at the start of a `routePrefix` is only left out when a slash follows.
  - The `id` of an API and each part of its `routePrefix` are checked by `RouteValidator` with the same function, in place of the `id`'s own expression in `registry-loader.ts`.
- **FR-002:**
  - `buildEntry` makes `segments` and `routePath` lowercase, and finds `index` in any letter case; `filePath` stays as it is on disk.
  - `languagePrefix(language, defaultLanguage)` in `src/core/content/route-path.ts` gives the lowercase prefix for the loader, the API pages, the canonical URL and the search index.
  - `buildLangPrefix`, `detectCurrentLang` and `stripLangPrefix` in `src/app/lang-utils.ts` use the lowercase language, and find it in a URL in any letter case; `<html lang>` and the search index folder keep the language as written.
  - `routePrefixFor` gives a lowercase prefix.
- **FR-003:**
  - Fallback pages are found by the lowercase `routePath`.
- **FR-004:**
  - `RouteMap` in `src/core/content/route-map.ts` has every page by its `routePath`: the pages of all languages, fallback pages and API operations together.
  - `RouteValidator` checks that a page's `routePath` isn't in the map before the page is added, in place of `detectCollisions` and `checkRouteCollisions`, and reports every page that has the same one, with both files or the API operation.
  - Two fallback pages in one language with the same `routePath` aren't reported, because their default-language pages are.
  - `RouteValidator` reports a folder in `public` that differs from a folder of a `routePath` only in letter case.
- **FR-005, FR-006:**
  - The API specs are loaded before the pages are transformed, so the `routePath`s of the operations are known.
  - `RouteMap` also has the `public` files, and its `resolve(path)` gives for a path the `routePath` or `public` file to use and, when it is wrong, the problem.
  - It leaves paths with a scheme, paths that start with `//` or `#` as they are, and compares `public` files by their exact names from the folder listing.
  - It decodes the path, because Markdoc encodes the path of a Markdown link.
  - An attribute type `RoutePath` replaces the path through its `transform()`, and a shared schema `validate()` reports the problem with the variable filled in; `href` of the `link` node and `path` of the `link`, `button` and `card` tags use both.
  - The `RouteMap` reaches Markdoc as a variable of the config, as `slugger` does, for pages and enrichment files.
  - `resolveNavigation` in `src/core/config/` replaces and checks the paths of the side, top and header navigation and the links in footer lines; side and top navigation paths must lead to pages of the default language.
  - It replaces the links in a footer line's translations in the same way, in the line they belong to and in its translated text, so translations are still found.
  - The check for wrong paths below an API prefix is removed from `nav-check.ts`.
  - The components example site has no link to a missing page.
- **FR-008:**
  - `mordoc build` stops on every problem with the level `error`, as it does for Markdoc.
  - Pages with the same `routePath` are reported together with the name problems and then stop `runPipeline`, in the build and the preview.
- **FR-009:**
  - The preview loads, resolves and checks navigation, header, footer and translations with the same function as the build, also after one of those files is saved.
  - `reparsePage` gets the `RouteMap`, made from the current pages, operations and `public` files.
  - The preview also watches `public`, and runs the full pipeline when a file there is added or removed.

## Decisions
- **D-001:** Names are checked with one regular expression, because the rule is fixed and short. Rejected: turning every name into a clean one with `slugify`, which gives `c` for both `C#` and `C++`, and nothing for names that aren't in Latin letters.
- **D-002:** The expression has no `i` or `u` flag, because together they also allow `K` (the Kelvin sign) and `ſ`.
- **D-003:** An error for a name that isn't allowed shows the characters that aren't allowed, and suggests a name only for `.MD`, because there is no other name that is surely correct. Rejected: suggesting a name with `slugify`.
- **D-004:** A page with a name that isn't allowed is left out of the preview, because its path can't work. Rejected: showing it at a path the build never has.
- **D-005:** Paths in pages are replaced and checked with Markdoc's attribute types and `validate()`, because Markdoc then gives the file and line. The check isn't in the type, because Markdoc doesn't check a value that comes from a variable. Rejected: walking the transformed page, where the line is lost.
- **D-006:** The descriptions in OpenAPI files are left as they are, because they belong to the API, as in `feat-markdoc-validation`. Rejected: checking them, which stops the documentation's build on another team's text.
- **D-007:** A problem in a navigation file names the file and the item's label, without a line, because the YAML parser doesn't give lines. Rejected: another YAML parser.
