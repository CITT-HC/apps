# apps

mini-apps

## Adding or changing a resource

`docs/apps.json` is the single source of truth for the cards on `docs/index.html`.
To add, change or reorder a resource, edit that file only. The page renders the
cards, the section headings and the jump links when it loads, so there is no build
step and no HTML to touch.

A section has an `id`, a `label`, a `navLabel`, an `icon`, a `palette` and a list of
`cards`. Sections appear in the order they are listed, on the page and in the hero
navigation. Palettes are `navy`, `green` and `blend`, all drawn from the FPDS blue
and green; a new section can reuse one of them without any CSS change.

A card needs a `title`, a `description` (inline links allowed), a `url`, a `cta`
label and a `thumb`. Set `"external": true` for anything that leaves the site.

Thumbnails are either a screenshot in `docs/img`:

    "thumb": { "kind": "image", "src": "img/aied.webp", "aria": "Browse the knowledge base" }

or a coloured badge, which is what a resource gets when it cannot be screenshotted,
such as a tool behind a sign-in:

    "thumb": { "kind": "badge", "icon": "course-badge", "label": "Canvas course", "aria": "…" }

Available badge and heading icons are named in `docs/apps.js`.

Descriptions are clamped to five lines so that every card in a row stays the same
height. A description longer than that gets a More toggle that expands it in place,
so a later edit cannot break the layout.

## How it is rendered

`docs/apps.js` fetches `docs/apps.json` and builds the page. Visitors without
JavaScript get the short fallback list in the `<noscript>` block of
`docs/index.html`.