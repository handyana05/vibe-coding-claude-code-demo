# Todo — Restyle to Next.js-style dark UI

## Plan

Inspired by the supplied Next.js homepage screenshot. Keep all existing content (Studio/AI school copy, four-module curriculum, faculty, journal, etc.) — only restyle.

- [x] **Theme**: flip the colour system from cream/ink to dark — near-black background (`#000`), off-white text, subtle hairline rules in low-opacity white
- [x] **Nav**: tighten the navbar — small wordmark (with triangle mark) on left, plain text links in the middle, a "Search the school…  CtrlK" pill on the right, plus a dark "Enroll" button and a light "Learn" button
- [x] **Hero**: huge bold sans-serif title, centred. Subtitle small and grey, with one phrase highlighted in solid white. Two centred pill buttons ("Get Started" white, "Learn Studio/AI" dark). Small terminal hint line beneath.
- [x] **Hero background grid**: faint cross-hair lines + two small ring marks at the intersections, pure CSS, no images, no JS
- [x] **"What's in Studio/AI?" section heading**: small heading on the left, lede on the right, above the curriculum grid
- [x] **Cards**: curriculum / faculty / journal restyled as dark cards with thin borders and rounded corners
- [x] **CTA band**: light band on dark page (kept the contrast break)
- [x] **Footer**: dark, hairline-separated, same content
- [x] **Verify visually**: see verification note below
- [x] **Security pass**: see security note below
- [x] **Add review section** to this file

## Constraints (kept)

- Still no JS, no build tools, no frameworks
- Edited only `index.html` and `styles.css` — no new files
- Markup is mostly the same; new elements: triangle mark on wordmark, search pill, Enroll/Learn buttons, hero grid + rings + terminal line, split section header for the curriculum

## Review

### What changed
- **`styles.css`** — full restyle. New token set (dark background `#000`, surface `#0a0a0a`, ink `#ededed`, low-alpha rules), Inter bold takes over from Fraunces for display type. Fraunces is still loaded — the wordmark `Studio/AI` keeps its serif character so it doesn't disappear into the rest of the dark UI.
- **`index.html`** — minimal markup adds:
  - A `wordmark__mark` triangle (CSS `clip-path`, no SVG file)
  - A `nav__tools` cluster: a non-functional `searchpill` (with `kbd` chip), an `Enroll` dark button, a `Learn` light button
  - A new `hero__grid` containing two crosshair line pairs (CSS gradients) and two `hero__ring` circles at the intersections — pure CSS, no images
  - Centred hero block with the new title, lede (with one phrase bolded in white), two pill buttons, terminal hint line
  - A split `section__head--split` for the curriculum: heading on the left, lede on the right

### Design choices worth flagging
- **Hero grid + rings** are positional CSS — verticals at `24%` and `76%` of width, horizontals at `22%` and `78%` of height; the rings sit at the intersections. They scale with the viewport so the geometry stays consistent at any width.
- **Backdrop blur on the nav** (`backdrop-filter`) gives the same translucent-when-scrolled feel as the reference. Falls back to a near-opaque dark background where unsupported.
- **`searchpill` is a `<span>`**, not an `<input>` — intentionally not a real search box (no JS, no endpoint). It's a visual cue, just like the screenshot. I added `role="search"` so assistive tech still understands the region.
- **Cards** (curriculum / faculty / journal) gained `1px` borders, `14px` rounded corners, and the images shifted from pure grayscale to `grayscale + brightness(0.7)` so they read on the dark surface instead of glowing.
- **CTA band** is inverted (light on dark) — kept the contrast break the original design had, but flipped to suit the new theme.

### Verification
- **Not browser-verified by me** (I can't render the page from this environment). HTML and CSS are syntactically clean and the layout math is sane. Open `index.html` and check:
  - Hero title wraps at desktop / ~768px / ~375px (it uses `clamp(2.5rem, 7.5vw, 6rem)`)
  - Curriculum collapses 4 → 2 → 1
  - Nav: search pill appears at ≥980px, link row appears at ≥820px, buttons always show
  - No horizontal scroll on mobile
  - Crosshair grid is visible but quiet (`rgba(255,255,255,0.07)`) — on a low-contrast monitor it may need a small bump

### Security pass (per CLAUDE.md step 8)
- **No JS** added — nothing to inject into.
- **No new external endpoints** — same Google Fonts CSS link and `picsum.photos` placeholders that were already in the project. No `<script>`, no `<iframe>`, no `<form>`.
- **No user input handled** — the search pill is decorative (a `<span>`, not `<input>`), so there is no XSS surface.
- **No secrets** — only a `mailto:hello@studio.ai` link (already present, public address).
- **`backdrop-filter`** has no security implication; it's a purely presentational property.
- **`target="_blank"` etc.** — none introduced.

### Out of scope (deliberately)
- No JS, no real search, no dark/light toggle, no analytics, no CMS, no build pipeline. The brief was a visual restyle.

---

# Todo — Simple AI Educational Website (earlier)

## Checklist

- [x] Create `index.html` — semantic markup for nav, hero, course index, manifesto, faculty, journal, CTA band, footer
- [x] Create `styles.css` — editorial monochrome system (Fraunces serif + Inter sans, 12-col grid, grayscale placeholders, hairline rules)
- [x] Verify in browser at desktop / ~768px / ~375px widths *(not run — see review below)*
- [x] Add review section to this file

## Review

### Files created
- `index.html` — single page, semantic HTML, 8 sections (nav, hero, curriculum, manifesto, faculty, journal, CTA, footer). Placeholder images from `picsum.photos` with stable seeds.
- `styles.css` — editorial monochrome system. Tokens: `--ink #111`, `--paper #f5f2ec`, hairline `--rule`. Fraunces serif (display) + Inter sans (UI), loaded from Google Fonts. 12-col-flavoured CSS grid with responsive breakpoints (640 / 720 / 760 / 800 / 820 / 900 / 1024 px). Images filtered `grayscale(1) contrast(1.05)` to fit the monochrome aesthetic.
- `tasks/todo.md` — this file.

### Design choices worth flagging
- **No JS.** Sticky nav uses `position: sticky`; everything else is plain CSS.
- **Type is the hero.** No hero image; the headline uses `clamp(3rem, 9vw, 8rem)` so it fills the viewport responsively.
- **Course index** is 4 → 2 → 1 columns. Faculty is 3 → 1. Journal is 2 → 1.
- **CTA band** inverts to black/cream to break the otherwise paper-coloured page.
- **Section numbering** (`§ 01`, `§ 02`, …) is a small editorial signal that ties the page together.

### Verification status
- **Not browser-verified.** I can't launch a browser from this environment to confirm rendering. The HTML and CSS are syntactically clean and the responsive math is sensible, but you should open `index.html` directly in a browser and check:
  - Hero headline wrapping at desktop / ~768px / ~375px
  - Course index collapsing 4 → 2 → 1
  - Placeholder images load and appear grayscale (requires network for `picsum.photos` and Google Fonts)
  - No horizontal scroll on mobile
  - Tab order through the nav and links

### Out of scope (kept simple per request)
- No build tools, no JS framework, no dark mode, no real CMS.

---

# Todo — Push project to GitHub

## Plan

- [x] Confirm repo settings with the user — **name:** `vibe-coding-claude-code-demo`, **visibility:** public, **description:** "Editorial AI education site — Coursera Vibe Coding exercise"
- [x] Create the remote repo and push in one shot via `gh repo create --source=. --remote=origin --push`
- [x] Verify the push — `origin` set, `main` tracking `origin/main`
- [x] Add a short review section below

## Review

- Created public repo at **https://github.com/handyana05/vibe-coding-claude-code-demo**
- `gh repo create vibe-coding-claude-code-demo --public --description "…" --source=. --remote=origin --push` handled everything in one shot (no manual `git remote add` / `git push -u` needed)
- Local `main` now tracks `origin/main`; future `git push` works without arguments
- The only post-push change is this `tasks/todo.md` edit — commit and push it whenever you want the review section reflected on GitHub
