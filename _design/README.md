# Design target for the site recode

These four files are the approved page designs (October 2026), exported from the "Young Lab Home Directions" design canvas. Open them in a browser and match them; they are the visual target, not code to copy. Jekyll ignores this folder, so nothing here publishes.

- `home.html`: hero (headline, lead, buttons; round seal right), Research Areas cards, Latest articles rows, parts bar
- `research.html`: "On this page" sidebar; sections in the order Research, Applications, Resources, Perspectives. Research and Applications are expandable rows (name left, one-line summary right)
- `people.html`: centered PI hero, member rows, alumni panel
- `join.html`: centered header, four path cards

Publications is not redesigned; keep it.

## Task

Recode `assets/css/style.css` and the page markup into one clean design system. Read `CLAUDE.md` first: the page-key rule (`--key` set per page on `<body>` from its tab color, and components use only `var(--key)`) and the page sections describe the target.

- One component per pattern: panel, card, row, pill/button, section heading.
- Remove dead rules (old research map, reading list, funding chips, home panels) and the stacked override blocks appended in the last session.
- Pages scale with the window: base font size grows with viewport width, and content uses percentage widths, not fixed caps.
- Check each page with `bundle exec jekyll serve --future --force_polling` at 1440px and 390px widths against these files before showing Eric.
- Don't commit; Eric pushes.
