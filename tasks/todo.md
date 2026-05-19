# Todo — Simple AI Educational Website

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
