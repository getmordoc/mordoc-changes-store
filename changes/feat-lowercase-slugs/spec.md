# Lowercase page paths from file names: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The reader opens the page of `Guide/Image_Sizes.md` at `/guide/image_sizes`.
- **AC-002:** The author writes a path in any letter case, such as `/Image` or `/image` for `Image.md`, and the link in the built site goes to `/image`.
- **AC-003:** The author sees an error when a file or folder name isn't allowed, such as `Media Foo.md` or `C#.md`.
- **AC-004:** The author sees an error when two pages have the same path, such as `Image.md` and `image.md` in one folder.
- **AC-005:** The author sees an error when a path in the navigation, in the footer or in a page leads to no page or file.
- **AC-006:** The reader sees `de/image.md` as the translation of `en/Image.md`.
- **AC-007:** The author sees the same paths and errors in the preview as in the build, also after saving a file.
- **AC-008:** The author can fix a name or a path while the preview keeps running.

## Functional Requirements

### FR-001: Names of pages and folders
The name of a page, without `.md`, and the names of the folders it is in contain only letters `a-z` and `A-Z`, digits, hyphens and underscores. They start with a letter or a digit. Any other name gives an error.

- The `id` of an API and each part of its `routePrefix` follow the same rule, because they are in the paths of its pages.
- Files and folders whose name starts with a dot are skipped, such as `.obsidian`.
- A file that ends in `.md` in another letter case, such as `FOO.MD`, gives an error that asks to rename it.

### FR-002: Lowercase paths
The path of a page is its folder and file names in lowercase: `Guide/Image_Sizes.md` gets `/guide/image_sizes`. The built folders, the sitemap and the URL given to search engines use this path.

- A file named `index`, in any letter case, is the page of its folder.
- The language in a path is lowercase, such as `/pt-br` for `pt-BR`.
- The `id` and the `routePrefix` of an API are lowercase in the paths of its pages.

### FR-003: Translations
Pages are translations of each other when their paths are the same without the language: `/guide` and `/de/guide`.

### FR-004: Unique paths
No two pages have the same path, over all languages and API pages together. When they do, an error names both files, or the file and the API operation.

- A folder in `public` gives an error when its path differs only in letter case from a page's path or from the start of it, such as `public/Images` and `/images/logo`. Some systems would put the page in that folder.

### FR-005: Paths in any letter case
A path that the author writes finds its page in any letter case, and the built site uses the page's lowercase path. This covers the side, top and header navigation, the footer, and links, buttons and cards in pages and in the texts for the API reference.

- A slash at the end of the path is ignored: `/guide/` finds `/guide`.
- Anything from a `?` or `#` is kept as written: `/Guide#Top` becomes `/guide#Top`.
- A variable in a path is filled in first.

### FR-006: Paths lead to a page or file
A path of FR-005 leads to a page or to a file in `public`. When it doesn't, the author sees an error.

- A path to a file in `public` has the same letter case as the file.
- A path to a folder in `public` with an `index.html`, such as `/demo/`, leads to that file.
- A path in the side or top navigation gives an error when it leads to a page in another language than the default, such as `/de/guide`.
- A path to another website, such as `https://example.com`, and a link to a heading on the same page, such as `#top`, aren't checked.
- A path to a page of an API isn't reported when the API's OpenAPI file can't be loaded, because that file has its own error.
- A path without a slash at the start, such as `image`, `./image` or `google.com`, gives an error that asks for a slash at the start, or for `https://` when it is another website.

### FR-007: Clear errors
Each error names the file, what is wrong and, when there is one, the correct name or path. The author sees all name and path errors in one list.

### FR-008: When errors stop Mordoc
A name or path error stops the build. The preview shows the error and keeps running.

- Two pages with the same path stop the preview when it starts.
- When two pages get the same path later, the preview keeps running.

### FR-009: Errors in the preview
The preview checks names and paths when it starts and after each saved file. It uses the same lowercase paths and shows the same errors as the build.

## Non-Functional Requirements

### NFR-001: The same on every system
The same site gives the same paths and errors on macOS, Linux and Windows.

## Boundaries
- The author's files are never changed, because they belong to the author.

## Constraints
- It is released in Mordoc 2.2.0, together with `fix-trailing-slash-current-link` and `fix-file-links`.

## Risks
- Authors lose pages and texts for the API reference that are symbolic links, because Mordoc no longer follows these links in `content` and in the folders with these texts. The release notes say this.
- Authors can't build an existing site after this minor update until they rename files that aren't allowed and fix paths that lead to no page or file. The release notes say this.
- Readers get "page not found" from links on other websites to a page with capital letters in its path, on hosts that find files case-sensitively.
- Readers who type capital letters in a page's path still get "page not found" on hosts that find files case-sensitively.

## Open Issues
- None
