# Lowercase page paths from file names: QA Plan

**Change:** `feat-lowercase-slugs`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Build tests in `test/build/` run the Mordoc command line on test sites, as `validation.test.ts` does.
- The pattern that finds problems in the output also accepts file names with spaces and problems without a line.
- Preview tests start `mordoc dev` on a copy of a test site in a temporary folder, save files, and read the problems it prints.
- A browser test in `test/e2e/components.spec.ts` runs on the components example site, in light and dark.
- The existing tests keep passing.
- `../mordoc-docs` (English and German) builds with this branch, with the same paths as on `main`.
- Run `npm ci` on Node.js 24, then `npm run check` and `npm test`.

## Test Coverage
- **AC-001:** The test site has `Guide/Image_Sizes.md`, an `Index.md` in a folder, a file name that starts with a digit, the language `pt-BR` and an API with capital letters in its `id`. The built folders, the sitemap and the canonical URLs are lowercase. The language picker and the search find the German and Portuguese pages.
- **AC-002:** The test site has paths in another letter case than their page, such as `/Guide` for `guide.md` and `/guide/image_sizes` for `Guide/Image_Sizes.md`, some with a slash at the end, a `?` or a `#`. They are in the side, top and header navigation, the footer and its translation, a Markdown link, a `link` tag, a `button`, a `card`, a variable and an enrichment file. Every link in the built pages is the lowercase path. In the browser, a page opened from a path in capitals is marked in the sidebar. A link in the description of an OpenAPI file stays as written, also when `variables.yaml` has a variable named `routeMap`.
- **AC-003:** The test site has `Media Foo.md`, `C#.md`, `v2.1.md`, `-foo.md`, `_foo.md`, a name with `é` in one and in two characters, a name with the Kelvin sign, `FOO.MD`, a folder with a space and an API prefix with a space. Each is reported once, with its file, and the build stops. `.hidden.md`, `.obsidian/b.md` and a broken link named `.#callouts.md` give no page and no error.
- **AC-004:** The test site has `setup.md` with `setup/index.md`, `en/de/setup.md` with `de/setup.md`, and a page with the same path as an API operation. Each error names both, and the build stops. `Image.md` with `image.md` gives the error where the file system allows both. `public/Images/` with `images.md` is reported, and `public/images/` isn't.
- **AC-005:** The test site has a wrong path in each place of AC-002, the paths `image`, `./image` and `google.com`, a file in `public` in another letter case, and a path to a page of another language in the side navigation. Each is reported, and the build stops. A file in `public`, a folder in `public` with an `index.html`, other websites, `mailto:`, `#heading` and a page of an API whose OpenAPI file can't be loaded aren't reported. A problem on a page that is also shown in other languages is reported once.
- **AC-006:** The test site has `en/Image.md` and `de/image.md`. They give `/image` and `/de/image`, each with its own text.
- **AC-007:** `mordoc dev` prints the same problems as `mordoc build` for the sites of AC-003 and AC-005. It prints them again after a page, a navigation file or a translation is saved, and after a page or a file in `public` is added or removed. By hand: the paths in the preview are the same as in the build, also after a file is renamed only in letter case.
- **AC-008:** While `mordoc dev` runs, a wrong path and a name that isn't allowed are reported, and the preview still answers. After they are fixed, they aren't reported again. Two pages with the same path stop the preview when it starts, and it keeps running when they get the same path later.
- **NFR-001:** `npm test` gives the same results on macOS and Linux. Windows is tested by hand, or reported as not tested.
