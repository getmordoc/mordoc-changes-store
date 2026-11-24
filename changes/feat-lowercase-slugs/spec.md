# Lowercase page paths from file names: Specification

**Proposal:** [proposal.md](./proposal.md)

## Acceptance Criteria
- **AC-001:** The reader opens the page of `Guide/Image_Sizes.md` at `/guide/image_sizes`.
- **AC-002:** The author writes a path in any letter case, such as `/Image` or `/image` for `Image.md`, and the link in the built site goes to `/image`.
- **AC-003:** The author sees an error when a file or folder name isn't allowed, such as `Media Foo.md` or `C#.md`.
- **AC-004:** The author sees an error when two pages have the same path, such as `Image.md` and `image.md` in one folder.
- **AC-005:** The author sees an error when a path in the navigation or in a page has no page or file.
- **AC-006:** The reader sees `de/image.md` as the translation of `en/Image.md`.
- **AC-007:** The author sees the same paths and errors in the preview as in the build, also after saving a file.
- **AC-008:** The author can fix a name or a path while the preview keeps running.

## Functional Requirements
- **FR-001:** The names of pages, without `.md`, and of the folders they are in contain only letters `a-z` and `A-Z`, digits, hyphens and underscores, and start with a letter or a digit.
  - This also applies to an author's own part of an API page's path.
  - Files and folders whose name starts with a dot are skipped.
  - A file that ends in `.md` in another letter case, such as `FOO.MD`, gives an error that asks to rename it.
- **FR-002:** The path of a page is its folder and file names in lowercase, also in the built folders, the sitemap and the URL given to search engines.
  - A file named `index`, in any letter case, is the page of its folder.
  - The language, such as `/pt-br` for `pt-BR`, and the author's own part of an API page's path are also in lowercase.
- **FR-003:** Pages belong together as translations when their paths are the same without the language.
- **FR-004:** No two pages have the same path, over all languages and API pages together. The error names both files, or the file and the API operation.
  - A folder in `public` whose path differs from a page's path, or from the start of it, only in letter case gives an error, because some systems put the page in that folder.
- **FR-005:** A path to a page is found in any letter case, and the built site uses the page's lowercase path. This covers the side, top and header navigation, the footer, and links, buttons and cards in pages and in the texts for the API reference.
  - A slash at the end of the path is ignored, and anything from a `?` or `#` is kept as written.
  - A variable in a path is filled in first.
- **FR-006:** A path to a page in the navigation or in a page leads to an existing page or a file in `public`. Other websites and links to a heading on the same page are left as they are.
  - A path without a slash at the start, such as `image`, `./image` or `google.com`, gives an error that asks for a slash at the start for a page or file of the site, or `https://` for another website.
- **FR-007:** Each error names the file, what is wrong and, when there is one, the correct name or path. All name and path errors are reported together.
- **FR-008:** Errors stop the build. The preview reports name and path errors and keeps running; two pages with the same path stop it when it starts.
- **FR-009:** The preview applies the same rules when it starts and after each saved file.

## Non-Functional Requirements
- **NFR-001:** The same site gives the same paths and errors on macOS, Linux and Windows.

## Boundaries
- The author's files are never changed.

## Constraints
- It is released in Mordoc 2.2.0, together with `fix-trailing-slash-current-link`.

## Risks
- Symbolic links in `content` and in the folders with texts for the API reference are no longer followed, so the release notes say this.
- Existing sites stop building after a minor update of Mordoc, until they rename files that aren't allowed and fix paths without a page, so the release notes say this.
- The path of a page with capital letters in its name changes, so links to it from other websites stop working on hosts that find files case-sensitively.
- A reader who types capital letters in a page's path still gets "page not found" on hosts that find files case-sensitively.

## Open Issues
- None
