# Young Lab Website — CLAUDE.md

## Project Overview

Jekyll-based GitHub Pages site for the Young Lab at Worcester Polytechnic Institute.
URL: https://emyounglab.github.io

**Research focus:** Synthetic biology, metabolic engineering, nonconventional yeasts, microbial communities, biosensors.

---

## Local Development

```bash
bundle install
bundle exec jekyll serve --future --force_polling
# Visit http://localhost:4000
```

`--future` shows future-dated posts (also enabled via `future: true` in _config.yml).
`--force_polling` is required on Windows (Git Bash) for file-change watching to work.

Build only:
```bash
bundle exec jekyll build
# Output in _site/
```

**Note:** Always use `bundle exec` — do not run `jekyll` directly, as it may use a different system version.

---

## Project Structure

```
_config.yml          # Site title, URL, plugins, future: true
Gemfile              # Ruby gem dependencies (github-pages ~> 232, minima ~> 2.5)

_layouts/
  default.html       # The only layout; every page names it. Sets <body class="key-…"> and the <main> column

                     # NOTE: the whole Projects system is retired. The _projects
                     # collection, _layouts/project.html and the collections: block
                     # went 2026-08-25; projects.md and _data/projects.yml went
                     # 2026-08-29. All of it duplicated the research page and none of
                     # it was in the nav. Files sit in _to_delete/ until removed by hand.

_includes/
  nav.html           # One row: red wordmark block, header image, tabs (from one list) on the key bar
  footer.html        # WPI logo, copyright
  toc.html           # "On this page" panel from page.toc front matter (Research, Publications, People)
  pub-item.html      # Publications page entry: title, authors, venue, DOI, tags
  news-item.html     # One news row: date, title, text, optional "Read more" (field: url)

_design/              # Design targets (home/research/people/join.html, README.md), excluded from the build
  tabled.md          # Text the targets had no place for, verbatim
  shots/             # Site vs target screenshots, 1440 and 390

_data/               # YAML content files — edit these to update site content
  people.yml         # PI, students, staff, alumni
  publications.yml   # All publications (journal, preprint, book-chapter)
  news.yml           # News items (sorted newest-first on news.md)
  resources.yml      # Part kits, software, biofoundries, funding: Research Resources cards + Home parts bar

assets/
  css/site.css      # The design system: tokens, page key, components (see Design System)
  img/
    young_header.png # Header image, right of the wordmark block
    (home hero uses favicon/favicon.png, the same seal image)
    people/          # Person photos
    logos/
      wpi_logo.png   # WPI logo (available for use in layouts)
    favicon/         # Full favicon set — all wired into default.html <head>
      favicon.ico
      favicon.svg
      favicon-96x96.png
      favicon.png
      apple-touch-icon.png
      web-app-manifest-192x192.png
      web-app-manifest-512x512.png
      site.webmanifest

Pages (Markdown):
  index.md           # Home: hero, area cards, 3 latest articles (dynamic), parts panel
  research.md        # TOC panel + area rows, application rows, Resources, Perspectives
  people.md          # "People" heading, PI card, member rows, alumni panel, all from people.yml
  publications.md    # Renders publications.yml grouped by year/type
  news.md            # news.yml as rows, newest first (not in the nav)
  join.md            # Recruitment info for PhD, undergrad, postdoc, collaborators
```

---

## Design System

### Fonts (Google Fonts)
- **Body:** DM Sans (400, 500, 700 for small uppercase labels)
- **Headings & site title:** DM Serif Display, weight 400 (no faux bold)
- Two families only. Inter was removed 2026-10-02; Publications now uses DM Sans.

**Visual target:** the "Final" page of the "Young Lab Home Directions" design
canvas (claude.ai/artifact/PDxHL82qhm3vLthKvyiW2n): Home, Research, People, Join.
Publications keeps its list behavior and tags; its wrapper was rebuilt on the system 2026-10-02. **Mockup text is approved copy** (headings,
sentences, button labels): use it. **Lists come from the data files** (alumni,
members, publications, venues): the mockups show samples, not counts.
Settled by Eric 2026-10-02. Tokens and brand book: the "Young Lab" design
system artifact (claude.ai/artifact/Vp7KR5c4z2jWeqDAeKRF2L).

### Colors (CSS variables in site.css)
Palette inspired by the Time Variance Authority (TVA) from Loki — retro-bureaucratic, mid-century modern feel.

| Variable | Value | Usage |
|---|---|---|
| `--red` | `#AC2B37` | WPI Red — wordmark block; Home key |
| `--orange` | `#C97720` | TVA burnt orange — Research key |
| `--green` | `#556B4A` | Dark sage — People key |
| `--navy` | `#1E2E4A` | Deep navy — Publications key (and the default) |
| `--blue` | `#5E8FAF` | Dusty slate blue — Join key; Publications links, numbers, year stamps |
| `--blue-dark` | `#3F6A87` | Blue at heading size on the Join page |
| `--fg` | `#1a1a1a` | Body text |
| `--muted` | `#6B6457` | Secondary text (roles, authors, meta) |
| `--bg` | `#F8F5EF` | Page background (warm off-white) |
| `--bg2` | `#EDE9E2` | Warm cream — cards, footer background, light text on dark backgrounds |
| `--line` | `#D4CCBF` | Warm tan — borders, dividers |

### Page colour keying
**The nav tab colour keys the page.** Each page uses its tab colour as its accent;
other palette colours appear only where genuinely needed, and sparingly.

| Page | Key colour |
|---|---|
| Home | `--red` |
| Research | `--orange` |
| People | `--green` |
| Publications | `--navy` |
| Join | `--blue` |

**Mechanism (2026-10-02).** Each page's front matter sets `key: red|orange|green|navy|blue`;
`default.html` puts `class="key-<key>"` on `<body>`, and `.key-*` defines four
variables. Components use only these, never a hue name:

| Variable | Use |
|---|---|
| `--key` | fills, rules, edges, h1, +/− markers |
| `--key-head` | h2, h3, card titles (Join: `--blue-dark` #3F6A87) |
| `--key-link` | link text. Red/green: the key. Orange/blue: ink `--fg` with a key underline, because those hues fail at body size (orange 2.81:1 on cream). Navy (Publications): `--blue`, as before |
| `--key-hover` | link hover |

Hue names appear only in the nav tabs and the header wordmark block. The nav bar
and footer rule take `--key`. Do not "fix" orange headings to navy for contrast.

**Pages scale with the window.** The root font size is fluid (15px at phone width,
16px at 1440, capped at 20px) and component sizes are in rem. Front matter
`wrap: full|wide|narrow` puts the page in the `.wrap` column at 88% / 86% / 68% of
the window (Home / Research, Join, Publications, People / News, 404), with no fixed caps.
Every page uses `.wrap`; the default is `wide`. The old `.container` layout is gone.

The stylesheet is `assets/css/site.css`, not `style.css`: with no `theme:` set,
GitHub Pages' default theme also writes `assets/css/style.css`, and the two
collided during local rebuilds (renamed 2026-10-02). `_design/` is in `exclude`
so files dropped there don't trigger rebuilds.

### Tokens (site.css §1)
Components use tokens only; no raw sizes below the header.
- **Type** `--fs-2xs` .75 · `--fs-xs` .875 · `--fs-sm` .9375 · `--fs-md` 1 ·
  `--fs-lg` 1.1875 · `--fs-xl` 1.375 · `--fs-2xl` 1.5 · `--fs-3xl` 2 (h2) ·
  `--fs-4xl` 3.25 (h1) · `--fs-5xl` 4 (home headline), all rem.
- **Space** `--sp-1` .375 · `--sp-2` .625 · `--sp-3` .75 · `--sp-4` 1 · `--sp-5` 1.25 ·
  `--sp-6` 1.5 · `--sp-7` 2 · `--sp-8` 3 · `--sp-9` 4 · `--sp-10` 5, all rem.
- `--radius`, `--pill`, `--rule` (1px tan line), `--edge` (4px).
- The header and footer are a fixed brand bar in px, on purpose. The stamped
  type tags in §7 keep a few px values for their look.

### Components (site.css §5) — one per pattern
- **Section** `.section` stacks a heading (plain `h2`) over its content;
  `.section-narrow` (82%, centered), `.section-more` (centered link after it).
- **Label** `.label` small caps, muted; `.label-key` puts it in the page key.
- **Pill** `.btn` (filled key) and `.btn-outline`; `.btn-sm`; `.pills` lays out a row.
  Pill padding is in em so it scales with its own text.
- **Panel** `.panel` (cream block holding a section); `.panel-bar` lays it out in a row.
- **Edge** `.edge`: key-colour top rule, on a panel or a card.
- **Grid** `.grid`: auto-fit columns no narrower than `--min` (15rem; `.grid-sm`
  12.5rem). Holds cards, and the alumni list (`.grid.alumni`).
- **Card** `.card`: `.title` (the title element, also used in `.media`), `.card-links`. A card that leads with
  `.label.label-key` shows its title in ink. A linked `a.card` lifts 2px on hover.
- **Row** `.row` in `.rows`: ruled grid line, `.row-term` then `.row-body`.
  `.rows-dated` (5.25rem year column), `.rows-split` (40%), `.rows-plain` (term as a small
  dateline, News), default 15rem.
  `<details class="row">` adds a +/− marker and expands to `.row-more`.
- Page pieces (§6): `.hero` (Home); `.intro` centered opener (Join, 404); `.media` image beside text (PI card);
  `.toc` panel beside `.toc-main` (Research).
- Utilities: `.meta` (small muted line), `.lede`, `.muted`, `.center`.
- Paragraphs have no margins (one base rule); containers space children with `gap`.
- `.media` (image beside text) is self-contained; on the PI card it sits on a `.panel`.

Add a modifier to an existing component before adding a new class. No inline styles.

### Structure rules
- Every page sets `layout: default` explicitly. Do not rely on `defaults:` in
  `_config.yml`: `jekyll serve` skipped them for 404.html while `jekyll build`
  applied them (seen 2026-10-02).
- Active nav tab is styled from `aria-current`, set in `nav.html`; there is no
  `.active` class.
- "On this page" panels come from `_includes/toc.html`, fed by `toc:` front matter on
  Research, Publications and People (Publications passes its years in). Each `id` must match a
  section or row id on the page.
- Resource links live once, in `_data/resources.yml`. A link with a `home:` label
  also appears on the Home parts bar.

### Header Layout
- One row (option B of `_design/header-options.html`, chosen by Eric 2026-10-04): red
  wordmark block, `young_header.png` at 90px, then the tabs right-aligned, all on a 4px
  `--key` bar. Header is 94px, down from 150px. Tabs come from one list in `nav.html`
- At 1160px and below the tabs drop to a second row (grid), as before; the breakpoint
  leaves room between the image and the Home tab at 19px tab type
- Sticky above 600px; below it the header scrolls away and the tabs shrink to fit one line at 390px

### Research Page
**Rebuilt 2026-10-02 to the Final canvas.** The navy map, its arcs script and the
`EDGES` array are gone. Layout: an "On this page" `.panel.edge.toc` beside
`.toc-main`, which holds four sections:

1. **Research** (`#areas`): h1, lede, then four `<details class="row">` —
   `#metabolic-engineering`, `#circuits`, `#onboarding`, `#biofoundries` (this order
   everywhere: rows, TOC, Home cards; set by Eric 2026-10-02). The
   summary shows the canvas one-liner; `.row-more` holds the full prose, unedited.
   The one-liners restate each body's opening, so an open row hides its summary
   line (CSS) and shows only the full text. Never trim a body's first sentence to
   avoid the repeat: keep every body complete. Applies to Applications rows too.
2. **Applications** (`#applications`): five rows — `#app-soil-sensing`,
   `#app-biomanufacturing`, `#app-medicines`, `#app-biomaterials`,
   `#app-biosecurity`. Each body ends with a `.meta` "Draws on" line naming the
   areas that feed it.
3. **Resources** (`#resources`): four cards — `#part-kits`, `#software-projects`,
   `#organizations` (titled Biofoundries), `#funding`.
4. **Perspectives** (`#reviews`): labelled cards for every non-training review and
   book chapter, rendered from publications.yml.

Anchor IDs are unchanged from the map version, so old deep links still work.

**Papers are inline links on the claims they support**, not citation lists. An
earlier version generated a publication list per area with Liquid; it read as a
second copy of the publications page and was removed. Full citations live on
`publications.md`. Every area-tagged paper is linked in prose (verified 2026-10-02) —
audit with: every `doi` in `publications.yml` that has `areas` should appear in
`research.md`.

**Prose structure.** One organism per paragraph with a bolded lead-in
(Metabolic Engineering), and named facilities integrated into the paragraph
whose claim they support — CREATE under Automation, BioHub under Scale. Do not
add standalone `<h3>` blocks for organisations; they read as disconnected.

**Collaborations are a rule, not a group.** Each area names who it works with in
a `.meta` line. Do not create a Collaborations section.

**Expanding rows.** Any in-page link opens its target `<details>`, and a deep link
like `/research/#app-biosecurity` opens on load (the small inline script).
Rows stack to one column below 600px.

- Prose is Eric's own text, recut. Do not rewrite it without asking; the register
  is deliberate (peers and collaborators, method first, no premise-explaining).
- The Projects system is retired (2026-08-29). Do not recreate `projects.md`,
  `_data/projects.yml`, or a `_projects` collection. Research areas and
  applications live on `research.md` and nowhere else.
- Two different Massachusetts funders, and they are not interchangeable. The
  **BioHub** was launched with $5.2M from the **Massachusetts Technology
  Collaborative**. **CERES** came from the **Massachusetts Life Sciences Center**
  Building Breakthroughs award. Corrected by Eric 2026-08-28 after an audit
  wrongly called them one inconsistency.
- The Genetic Circuits section is knowingly the thinnest-sourced on the page: the
  patent is the only citation. It stays as written until the DARPA-cleared
  preprint lands. Do not paper over it. Decided 2026-08-28.

### Publication tagging
Two independent fields on each `_data/publications.yml` entry, added 2026-08-25:

```yaml
areas:   [onboarding, metabolic-engineering, circuits, biofoundries]   # 0+, subject
context: [training, collaboration]                                      # 0+, provenance
```

`biofoundries` is the whole area — software and bioinformatics, automation, and
scale. Bioinformatics work belongs here; there is no separate slug for it. The
*Candida auris* paper is `biofoundries` because it was a PRYMETIME collaboration,
not because it is foundry infrastructure (Eric, 2026-08-29). It also carries
`onboarding`, added by Eric 2026-10-02; it is listed under Genomes and
transcriptomes in the Organism Onboarding row.

**Rule: a training publication never carries an area.** Training means Eric's own
doctoral and postdoctoral work, before the lab. Those papers appear only in the
Prior work section, never under a research area.

Current counts: onboarding 9, biofoundries 11, metabolic-engineering 6,
circuits 2 (verified 2026-10-02). Context: 13 training, 12 collaboration, 14 current lab
(verified 2026-08-29).

**Rule: `areas` records why the lab was in the room, not what technique it used.**
Settled by Eric 2026-08-29 after this exact case came up twice.

- *C. auris* (Rao), probiotic yeast (Rao), episomal plasmids (Vickers) →
  `biofoundries`, because genome reading *was* the contribution.
- *K. delftensis*, *O. polymorpha* → `onboarding` only. Those genomes were built
  to onboard a yeast. PRYMETIME was incidental, so it earns no tag.

Do not retag the two reference genomes to `biofoundries`. It was proposed and
rejected 2026-08-29; the technique is not the reason.

**PRYMETIME usage is a separate record from the tags.** The Software Projects
section lists what the tool has done, in four groups: the *K. delftensis* and
*O. polymorpha* reference genomes, IARPA FELIX detection, the two Rao papers,
and the Vickers plasmid work. That list is not `areas` and does not have to
match it. PRYMETIME does not do transcriptomics, so the *X. dendrorhous* omics
onboarding and the oleaginous-yeast comparative transcriptomics papers are not
on it. The Vickers collaboration is finished &mdash; do not write it as ongoing.
Circuits is thin because the fungal-highways results are patented and the
preprint is pending DARPA approval.

The old `projects:` field is gone — it pointed at the deleted `_projects` pages.

### Publications page
Wrapper (2026-10-02): an "On this page" `.toc` panel listing the years and Prior
work, as on Research; h1 "Publications"; each year a `.section` with the year as
its h2 and a `.pub-list` of `pub-item.html` entries. `.toc-main-compact` keeps the
year sections closer than Research's. Entries, numbering and tags are unchanged.

Two sections (changed 2026-10-02 at Eric's direction):
1. **Lab work** — everything not `context: training`, reviews and chapters included,
   numbered and grouped by year. Type tags (Review, Book Chapter, Patent) carry the
   distinction. Rationale: pulling reviews out thinned the per-year output.
2. **Prior work** (`#prior-work`) — everything tagged `context: training`.

Reviews and chapters also appear on the research page as **Perspectives**
(`#reviews`), rendered as cards from publications.yml. It shows the lab as a voice
in the field. Funding is one sponsor line in the Resources Funding card.

### Content conventions
- `Software Projects` under Resources lists **PRYMETIME only**
  (github.com/emyounglab/prymetime). The other repos in the emyounglab org are
  paper supplements, not projects — do not list them. SBKS is Myers' project, not
  the lab's repo; it is described in the Software and Bioinformatics area instead.
- Author-name convention: Cassandra publishes under both Brzycki and Newton. All
  `publications.yml` entries use **C. Newton** so one person does not read as two.
  `people.yml` keeps the fuller "Dr. Cassandra Brzycki Newton" so readers who knew
  the earlier name can connect them.

### Home Page (`index.md`, key red)
- **Hero**: headline, lede, three pills (Our research filled; Publications and Join outlined), `favicon/favicon.png` clipped to a circle
- **Research Areas**: four `.card.edge` links to the research rows
- **Latest articles**: `.rows.rows-dated`, the first three journal articles or preprints in publications.yml
- **Get our parts and tools**: `.panel.panel-bar` of outlined small pills

### People Page (`people.md`, key green, wide, TOC: Principal Investigator / Current members / Alumni)
- **PI card** (redesigned 2026-10-02 so the page leads with the lab, not the PI): page h1 is "People"; then a compact left-aligned `.panel.edge.media`: 6rem round photo, "Principal Investigator" label, name, `bio:` (a people.yml field), then email and `links` in one meta line. Phone, address, affiliations and titles stay in the data but are not rendered.
- **Current members**: `.rows.rows-split` built from postdocs, students and staff, showing name, role and interests (first letter capitalized by CSS)
- **Alumni**: `.panel.edge` grid, "role → current"

### Join Page (`join.md`, key blue)
- Centered intro with an email pill, then four `.card.edge` cards: `#phd-ms`, `#undergraduates`, `#postdocs`, `#collaborators`. Copy is the mockup text; the old, longer copy is in `_design/tabled.md`.

---

## Writing register — Eric's voice

Derived from his own research summary and proposal text, 2026-08-29. The site's
prose should read as his. Match these, and do not "improve" past them.

**Do**

- Open with "We have developed…" and repeat the stem. He does not vary it for elegance.
- Use `can` as the capability verb: can grow, can support, can be transformed.
  Reserve `may` for real uncertainty.
- Gloss by apposition or parentheses: "the halotolerant yeast *D. hansenii*",
  "*Cupriavidus necator* (a potential platform host for biomaterial production
  from CO<sub>2</sub>)".
- Connect and conclude with `Thus,` `In fact,` `Furthermore,` `For example,`.
- State necessity flatly: "is necessary", "must have", "took a great deal of".
- Open a section with a problem statement when there is one — "Engineered model
  organisms rarely become commercially viable biofuel factories" — followed
  immediately by the mechanism.
- Repeat a distinctive word rather than swapping a synonym. His word is
  **actual** dry soil, not "real".
- End with significance when earned: "Thus, *D. hansenii* is an ideal organism for…".
- Keep his terms of art intact: "high-throughput combinatorial pathway
  engineering", "broad host range plasmid", "on-demand manufacture".

**Do not**

- Address the reader as "you", or ask a rhetorical question.
- Use antithesis for effect: "grown rather than manufactured", "invented at the
  bench rather than shipped elsewhere", mirrored clauses.
- Use an aphoristic opener with rhetorical timing ("X is only half the problem —").
- Use em-dashes for timing. He uses them almost never; parentheses instead.
- Write verbless labels or fragments as sentences.
- Use `lets` where he uses `enables`.
- Write empty bridge sentences ("The yeast work points the same way").
- Balance list items into matching grammatical shapes for their own sake.
- Hedge a claim he would assert.

**Passages that are near-verbatim his — never copyedit them.** The Genetic
Circuits paragraph; "Our key strategy is merging bioinformatics…"; the bacteria
part-library sentence; the *D. hansenii* and *X. dendrorhous* entries under
Metabolic Engineering; the first two sentences of Software and bioinformatics.
An edit to any of these is a rewrite request, not a copyedit — ask first.

A fuller sample lives outside the repo. Ask Eric for it before a prose pass.

---

## Key Conventions

- **CSS variables** in `:root` — always edit variables rather than hardcoding colors
- **Liquid indentation:** Do NOT indent Liquid tags with 4+ spaces in `.md` files — Markdown treats 4-space indentation as a code block. Use flush-left Liquid and `<h2>`/`<h3>` tags instead of `##` inside loops.
- **Responsive breakpoint:** 900px (grids collapse to single column)
- **Navigation links** are hardcoded in `_includes/nav.html`
- **No custom plugins** — must remain GitHub Pages safe (`plugins: []` in _config.yml)
- **Permalink style:** `pretty` (e.g., `/people/` not `/people.html`)
- **alumni** `current_position:` field in people.yml uses key `current:`

---

## Content Management

### Adding a person (`_data/people.yml`)
```yaml
- name: "First Last"
  role: "PhD Student"          # or Postdoctoral Researcher, Undergraduate, etc.
  email: "user@wpi.edu"        # optional
  website: "https://..."       # optional
  photo: "/assets/img/people/filename.jpg"  # optional
  interests: "topic one, topic two"         # optional string
```
Alumni go under the `alumni:` key with `current:` for their current position.

### Adding a publication (`_data/publications.yml`)
```yaml
- title: "Paper Title"
  authors: "Last A, Last B, Young EM"
  venue: "Journal Name"
  year: 2026
  type: journal                # journal | preprint | book-chapter
  doi: "10.xxxx/xxxxx"        # shown as text; title links to url
  url: "https://doi.org/..."   # link on title
  pdf: "/assets/pdf/..."       # optional
  tags: ["yeast", "CRISPR"]   # optional
```

### Adding a news item (`_data/news.yml`)
```yaml
- date: "2026-03-01"
  title: "News headline"
  text: "Short description."
  url: "https://..."           # optional "Read more" link
```

### Adding a research area or application (`research.md`)
Both are plain HTML in `research.md` — no collection, no data file. Each is a
`<details class="row" id="...">` whose `<summary>` holds a `.row-term` title and
a `.row-body` one-liner, followed by a `.row-more` div of `<p>`s. An application
ends with a `.meta` "Draws on" line linking its areas. Add the area to the TOC
panel, and for a new research area a card on `index.md`. Keep anchor IDs stable.

---

## Tasks

Last verified against the working tree: 2026-10-04

- [x] Recode site.css and the page markup into one design system to the Final canvas (Home, Research, People, Join). Verdict: done, uncommitted; 508 → 246 lines of CSS; checked at 1440 and 390 against _design/*.html, screenshots in _design/shots/.
- [x] Consistency audit, items 1–8 plus font normalization. Verdict: done, uncommitted; type and space tokens, News and 404 on `.wrap`, labels merged, `.grid` replaces `.card-grid`, `_data/resources.yml`, TOC in front matter, page.html and addgene-widget.html deleted, Inter removed; all seven pages checked at 1440 and 390.
- [ ] Update the "Young Lab" design system artifact tokens with the new type and space scales. Verdict: the artifact has neither.
- [ ] Decide each item in `_design/tabled.md` (restore, cut, or rehome). Verdict: the PRYMETIME uses list and the Addgene widget have no home in the canvas.
- [ ] Update the "Young Lab" design system artifact README: it still describes navy panels, red banners and left-border strips, which the canvas dropped. Verdict: the tokens are unchanged; only the shapes text is stale.
- [ ] Reconcile with the uncommitted rebuild on the other machine (emyoung). Verdict: that work never reached origin; discard it there before pulling this.
- [x] Build header option B (tabs in the band). Verdict: done 2026-10-04 on branch claude/exciting-ptolemy-jy9q29; checked at 1440, 1161, 1160, 700 and 390, no horizontal scroll.
- [ ] Remove the stale `.git/worktrees/head` folder by hand. Verdict: OneDrive locked it during cleanup; git no longer lists it.

## PI Contact

Eric M. Young — Associate Professor, Chemical Engineering, WPI
emyoung@wpi.edu | GP 4003, Life Sciences & Bioengineering Center, Gateway Park
