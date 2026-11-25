# Lowercase page paths from file names: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)

## Approach
- Built in `mordoc`.
- **FR-007:**
  - `BuildReport` in `src/core/build-report.ts` collects the problems of one run, prints them as one list, and stops the run when one is an error.
  - Each problem has a level and a message, and a file and line when there are any.
  - `BuildReport` has no Markdoc code.
  - `ContentValidator` in `src/core/content/content-validator.ts` validates Markdoc texts and adds the problems to `BuildReport`.
  - `RouteValidator` in `src/core/content/route-validator.ts` validates names and routes and adds the problems to `BuildReport`.
  - The heading of the list says that Mordoc found the problems.
  - `runPipeline` also prints the list when another error stops the run.
  - The pipeline creates the report and the validators before it loads the content, and passes a validator to each step that needs one.
  - `transformContent` validates no fallback pages.
- **FR-001:**
  - `validateName(name)` in `route-validator.ts` checks `/^[A-Za-z0-9][A-Za-z0-9_-]*$/`, and gives `{ valid: true }`, or `{ valid: false, error }` with the characters that aren't allowed.
  - `listMarkdocFiles` in `src/core/list-markdoc-files.ts` lists the Markdoc files for pages and for enrichment, sorted, with `.md` in any letter case.
  - `listMarkdocFiles` reads only files and folders, not symbolic links.
  - `listMarkdocFiles` skips a file when its name or one of its folders starts with a dot.
  - `RouteValidator` checks each folder and file name of a page with `validateName` and reports every problem.
  - `RouteValidator` reports a file that ends in `.md` in another letter case, with the new name when that name is allowed.
  - `loadContent` leaves out a page with a name problem.
  - `RouteValidator` checks the `id` of an API and each part of its `routePrefix` with `validateName`, in place of the `id`'s own expression in `registry-loader.ts`.
  - `routePrefixNames` in `src/core/openapi/slug.ts` leaves out a dot at the start of a `routePrefix` only when a slash follows.
- **FR-002:**
  - `buildEntry` makes `segments` and `routePath` lowercase, and keeps `filePath` as it is on disk.
  - `buildEntry` finds `index` in any letter case.
  - `languagePrefix(language, defaultLanguage)` in `src/core/content/route-path.ts` gives the lowercase prefix for the loader, the API pages, the canonical URL and the search index.
  - `buildLangPrefix`, `detectCurrentLang` and `stripLangPrefix` in `src/app/lang-utils.ts` use the lowercase language, and find it in a URL in any letter case.
  - `<html lang>` and the folder of the search index keep the language as written.
  - `routePrefixFor` gives a lowercase prefix.
- **FR-003:**
  - `loadContent` finds fallback pages by the lowercase `routePath`.
- **FR-004:**
  - `RouteMap` in `src/core/content/route-map.ts` has every page by its `routePath`: the pages of all languages, the fallback pages and the API operations.
  - `RouteValidator` checks that a page's `routePath` isn't in the map before the page is added.
  - `RouteValidator` reports every page whose `routePath` is already used, with both files, or the file and the API operation.
  - `RouteValidator` doesn't report two fallback pages in one language with the same `routePath`.
  - `detectCollisions` and `checkRouteCollisions` are gone.
  - `RouteValidator` reports a folder in `public` that differs from a folder of a `routePath` only in letter case.
- **FR-005:**
  - `RouteMap` has `resolve(path)`, which gives the `routePath` or the `public` file to use in the built site.
  - `resolve` decodes the path of a Markdown link.
  - `resolve` keeps a path with a scheme, and a path that starts with `//` or `#`, as it is.
  - The attribute type `RoutePath` in `src/core/content/schema/link-rules.ts` changes the path in its `transform()`.
  - `href` of the `link` node and `path` of the `link`, `button` and `card` tags have the type `RoutePath`.
  - The Markdoc config of pages and enrichment files has the `RouteMap` as a variable, as it has `slugger`.
  - The Markdoc config of the descriptions in OpenAPI files has no `RouteMap`, also when `variables.yaml` has a variable named `routeMap`.
  - `resolveNavigation` in `src/core/config/` changes the paths of the side, top and header navigation and the links in footer lines.
  - `resolveNavigation` changes the links in a footer line's translations, in the line they belong to and in the translated text.
- **FR-006:**
  - The pipeline loads the OpenAPI files before it transforms the pages.
  - `resolve` gives the problem when a path leads to no page or file.
  - `resolve` compares files in `public` by their exact names from the folder listing.
  - `RouteMap` gets the prefixes of the OpenAPI files that couldn't be loaded, and accepts every path below them.
  - The rule `pathExists` in `link-rules.ts` reports the problem from the schema's `validate()`, with the variable filled in, for the attributes with the type `RoutePath`.
  - `notInsideClickable` is in `link-rules.ts` too.
  - `resolveNavigation` reports the problems of the paths it changes.
  - `resolveNavigation` reports a side or top navigation path that leads to a page in another language than the default.
  - `nav-check.ts` has no check for wrong paths below an API prefix.
  - The components example site has no link to a page that doesn't exist.
- **FR-008:**
  - `mordoc build` stops on every problem with the level `error`.
  - `runPipeline` stops, in the build and the preview, when two pages have the same `routePath`, after it has collected the name problems.
- **FR-009:**
  - The preview loads, changes and checks the navigation, header, footer and translations with the same function as the build, also after one of those files is saved.
  - `reparsePage` gets the `RouteMap`, made from the current pages, operations and `public` files.
  - The preview watches `public`, and runs the full pipeline when a file there is added or removed.

## Decisions
- **D-001:** Names are checked with one regular expression, because the rule is fixed and short. Rejected: turning every name into a clean one with `slugify`, which gives `c` for both `C#` and `C++`, and nothing for names that aren't in Latin letters.
- **D-002:** The expression has no `i` or `u` flag, because together they also allow `K` (the Kelvin sign) and `ſ`. Rejected: both flags with `[a-z]`.
- **D-003:** An error for a name that isn't allowed shows the characters that aren't allowed, and suggests a name only for `.MD`, because there is no other name that is surely correct. Rejected: suggesting a name with `slugify`.
- **D-004:** A page with a name that isn't allowed is left out of the preview, because its path can't work. Rejected: showing it at a path the build never has.
- **D-005:** Paths in pages are changed and checked with Markdoc's attribute types and `validate()`, because Markdoc then gives the file and line. The check isn't in the type, because Markdoc doesn't check a value that comes from a variable. Rejected: walking the transformed page, where the line is lost.
- **D-006:** The descriptions in OpenAPI files are left as they are, because they belong to the API, as in `feat-markdoc-validation`. Rejected: checking them, which stops the documentation's build on another team's text.
- **D-007:** A problem in a navigation file names the file and the item's label, without a line, because the YAML parser doesn't give lines. Rejected: another YAML parser.
