# Lowercase page paths from file names: QA Plan

**Change:** `feat-lowercase-slugs`
**Tasks:** [tasks.md](./tasks.md)

## Test Strategy
- Build tests in `test/build/` run the Mordoc command line on test sites, as `validation.test.ts` does; the pattern for a problem also accepts file names with spaces and problems without a line.
- The preview tests start `mordoc dev` on a copy of a test site in a temporary folder, save files, and read the problems it prints.
- A browser test in `test/e2e/components.spec.ts`, on the components example site, in light and dark; the existing tests keep passing.
- Setup: `npm ci` on Node.js 24; run `npm run check` and `npm test`.
- `../mordoc-docs` (English and German) builds with this branch, with the same paths as on `main`.

## Test Coverage
- **AC-001:** A test site with `Guide/Image_Sizes.md`, `Index.md` in a folder, a file name that starts with a digit, the language `pt-BR` and an API with capital letters in its `id`: the built folders, sitemap and canonical URLs are all lowercase, and the German and Portuguese pages are found by the language picker and the search.
- **AC-002:** The same site has paths in other letter cases, such as `/Guide` for `guide.md` and `/guide/image_sizes` for `Guide/Image_Sizes.md`, in the side, top and header navigation, the footer and its translation, and in a Markdown link, a `link` tag, a `button`, a `card`, a variable and an enrichment file, some with a slash at the end, `?` or `#`: every link in the built pages is the lowercase path. In the browser, a page opened from a path written in capitals is marked in the sidebar.
- **AC-003:** A test site with `Media Foo.md`, `C#.md`, `v2.1.md`, `-foo.md`, `_foo.md`, a name with `é` in one and in two characters, a name with the Kelvin sign, `FOO.MD`, a folder with a space and an API prefix with a space: each is reported once, with its file, and the build stops. `.hidden.md`, `.obsidian/b.md` and a broken link named `.#callouts.md` give no page and no error.
- **AC-004:** `setup.md` with `setup/index.md`, `en/de/setup.md` with `de/setup.md`, and a page with an API operation: each error names both, and the build stops. `Image.md` with `image.md`, where the file system allows both. `public/Images/` with `images.md` is reported, and `public/images/` isn't.
- **AC-005:** A wrong path in each place of AC-002, `image`, `./image`, `google.com`, a file in `public` written in another letter case, and a path to a page of another language in the side navigation: each is reported. A file in `public`, other websites, `mailto:` and `#heading` aren't reported. A problem on a page that other languages fall back to is reported once.
- **AC-006:** `en/Image.md` and `de/image.md` give `/image` and `/de/image`, each with its own text.
- **AC-007:** `mordoc dev` prints the same problems as `mordoc build` for the sites of AC-003 and AC-005, and again after saving a page, a navigation file and a translation, and after adding and removing a page and a file in `public`. By hand: the paths in the preview are the same as in the build, also after renaming a file only in letter case.
- **AC-008:** While `mordoc dev` runs, a wrong path and a name that isn't allowed are reported and the preview still answers; after they are fixed, they aren't reported again. Two pages with the same path stop it when it starts; when they appear later, it keeps running.
- **NFR-001:** `npm test` gives the same results on macOS and Linux. Windows by hand, or reported as not tested.
