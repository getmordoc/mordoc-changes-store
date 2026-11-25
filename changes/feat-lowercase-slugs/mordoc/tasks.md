# Lowercase page paths from file names: Tasks

**Change:** `feat-lowercase-slugs`
**QA plan:** [qa.md](./qa.md)

## Tasks
- [x] **T-001 (FR-007): Collect all problems in one report**

  Collect every problem, from Markdoc and from Mordoc, in `BuildReport`. Print them as one list at the end of the run, also when another error stops the run.

- [x] **T-002 (FR-007): Report each problem once**

  Validate the file of a page only once. A mistake in an English page that is also shown in German is then reported once.

- [x] **T-003 (FR-001, FR-007, FR-008): Check the names of pages and folders**

  Add an error to `BuildReport` when the name of a page or folder isn't allowed, such as `Media Foo.md`. Leave that page out of the site.

- [x] **T-004 (FR-001): Check the names in an API's path**

  Add an error to `BuildReport` when the `id` or `routePrefix` of an API in `config/api.yaml` has a name that isn't allowed.

- [x] **T-005 (FR-001, FR-007, FR-008): Test the names**

  Write build tests for the errors of T-001 to T-004: each wrong name is reported once, with its file, and the build stops. Allowed names and names that start with a dot give no error.

- [x] **T-006 (FR-002, FR-003): Make the paths of pages lowercase**

  Make the path of a page from its folder and file names in lowercase. `Guide/Image.md` gets `/guide/image`, and `de/guide/image.md` is its translation.

- [x] **T-007 (FR-002): Make the paths of API pages lowercase**

  Make the `id` and `routePrefix` of an API lowercase in the paths of its pages. An API with the `id` `Shop` gets pages below `/api/shop`.

- [x] **T-008 (FR-002): Make the language lowercase in the build**

  Make the language lowercase in the paths of the built pages, the canonical URLs and the search index. The pages of `pt-BR` are at `/pt-br`.

- [x] **T-009 (FR-002): Make the language lowercase in the app**

  Make the language lowercase in the paths the app makes. Recognize the language in a URL in any letter case, such as `/pt-BR` and `/pt-br`.

- [x] **T-010 (FR-004, FR-008): Report two pages with the same path**

  Add an error to `BuildReport` that names both pages when they have the same path, over all languages and API pages. It stops the build, and the preview when it starts.

- [x] **T-011 (FR-004): Report folders in `public` that clash with a page**

  Add an error to `BuildReport` when a folder in `public` differs from a page's path only in letter case, such as `public/Images` and `/images`.

- [x] **T-012 (FR-002, FR-003, FR-004, FR-008): Test the paths of pages**

  Write build tests for T-006 to T-011: the built folders, sitemap, canonical URLs, translations and search index use the lowercase paths. Pages with the same path and clashing folders in `public` are reported.

- [x] **T-013 (FR-006): Load the OpenAPI files before the pages**

  Load the OpenAPI files before the pages are transformed, so Mordoc can check a link in a page to an API page.

- [x] **T-014 (FR-005, FR-006): Find the page or file of a path**

  Let `RouteMap` find the page or the file in `public` that a path leads to, such as the page `/guide` for `/Guide/`. When there is none, `RouteMap` gives the text of the error.

- [x] **T-015 (FR-005): Make links use the page's path**

  Change the path in Markdown links and in the `link`, `button` and `card` tags to the page's lowercase path in the built site. Do this in pages and enrichment files. Links in the descriptions of OpenAPI files stay as written.

- [x] **T-016 (FR-006): Report links without a page or file**

  Add an error to `BuildReport`, with the file and line, when a path of T-015 leads to no page or file.

- [x] **T-017 (FR-006): Remove the link to a page that doesn't exist**

  Delete the link to `/guide/does-not-exist` from the components example site, because it is now an error.

- [x] **T-018 (FR-005, FR-006): Test the links in pages and enrichment files**

  Write build tests for T-013 to T-016: a path in any letter case leads to the page, and a wrong path is reported with its file and line. Test each kind of link, a variable, and descriptions in OpenAPI files, also with a variable named `routeMap`.

- [x] **T-019 (FR-005): Make the navigation use the page's path**

  Change the paths in the side, top and header navigation to the page's lowercase path in the built site.

- [x] **T-020 (FR-005): Make the footer use the page's path**

  Change the links in footer lines to the page's lowercase path. Change them in the translations of these lines too, so each translation is still found.

- [ ] **T-021 (FR-006): Report wrong paths in the navigation and footer**

  Add an error to `BuildReport`, with the file and the label or footer line, when a path of T-019 or T-020 leads to no page or file. Also add an error when a path in the side or top navigation leads to a page in another language than the default.

- [ ] **T-022 (FR-006): Remove the old check for API paths**

  Remove the check for wrong paths below an API prefix from `nav-check.ts`, because T-021 replaces it.

- [ ] **T-023 (FR-005, FR-006): Test the paths in the navigation and footer**

  Write build tests for T-019 to T-022: paths in any letter case become the lowercase path, translated footer lines are still found, and each wrong path is reported.

- [ ] **T-024 (FR-005): Test a page opened from a path in capitals**

  Write a browser test on the components example site: a page opened from a path written in capitals is marked in the sidebar.

- [ ] **T-025 (FR-009): Check a saved page in the preview**

  When the author saves a page in the preview (`mordoc dev`), change its links to the lowercase path, and print an error for each link that leads to no page or file. Today the saved page shows its links as written, without errors.

- [ ] **T-026 (FR-009): Check a saved navigation file in the preview**

  When the author saves a navigation, header, footer or translation file in the preview, change its paths to the lowercase path, and print an error for each path that leads to no page or file. Today the preview only loads that file again.

- [ ] **T-027 (FR-009): Check all paths when `public` changes**

  When the author adds or removes a file in `public`, let the preview check the paths of the whole site again and print the errors. Today the preview doesn't notice this.

- [ ] **T-028 (FR-008, FR-009): Test the preview**

  Write preview tests for T-025 to T-027: after each change, the preview prints the same errors as `mordoc build` and keeps running. After the author fixes an error, it isn't reported again. Two pages with the same path stop the preview only when it starts.
