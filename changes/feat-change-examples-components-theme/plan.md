# Journey theme for the components example site: Technical Plan

**Proposal:** [proposal.md](./proposal.md)
**Specification:** [spec.md](./spec.md)
**QA plan:** [qa.md](./qa.md)

## Approach
- **FR-001:**
  - `config/site.json` has the name `Mordoc - Components` and describes it as an example website.
  - `config/variables.yaml` has `Components` as `productName`, a matching `supportEmail`, and `mapImage` for the route image.
  - `config/navigation/headernav.yaml` has Guide (link), Media (secondary) and Home (primary), all within the site.
  - `config/navigation/footer.yaml` describes the site and links to Mordoc on GitHub.
  - `content/en/index.md`, every page under `guide/` and `media/`, `README.md` and `package.json` have the new texts, keeping their tags and attributes.
  - External links go to real sites, `https://www.mordoc.dev` and `https://github.com/getmordoc/mordoc`, so they can be followed in tests.
- **FR-002:**
  - Each page keeps every tag, attribute and variation it has today; only the texts, labels and paths change.
  - The image inside a link is an image tag, the form Markdoc allows inside a link.
- **FR-003:**
  - `public/images/mordoc-hero.svg` is the home page hero background.
  - `public/images/route-map.jpg` (a route with four stops, 1080×608), `volcano.jpg` (1080×405) and `volcano-thumbnail.jpg` (640×360, the size of the clip) replace `orbit-map.svg` and `stars.svg`.
  - `public/videos/volcano.mp4`, a 3-second clip made for this site, replaces `orbit.mp4`.
  - `public/icons/` has the card icons from the Mordoc documentation and two diagram icons, named after their role.
  - `media/diagrams.md` has a sequence diagram about the journey, with the same syntax options as today.
  - The home page's section with a background image uses `route.svg`, a gold dashed route on a dark background, in place of `dots.svg`, because a section with a background image always gets white text.
  - `orbit-map.svg`, `stars.svg`, `orbit.mp4`, `dots.svg` and the old icons are removed, and `public/` only holds files the site uses.
- **FR-004:**
  - `config/styles/hero.css` gives the hero a light grey background (`#F1F2F0`) in light mode and a dark grey one (`#24282B`) in dark mode.

## Decisions
- **D-001:** Theme the site's content as a journey in four stops to a volcano, because it fits Mordoc's style without using names from existing stories. Rejected: keeping Orbit.
- **D-002:** Write every text and make every image for this site, because texts and images from existing works are protected by copyright. Rejected: quotes or images from existing works.
- **D-003:** Call the site Components, a neutral name, because names from existing stories are protected as trademarks. Rejected: a name from a story.
