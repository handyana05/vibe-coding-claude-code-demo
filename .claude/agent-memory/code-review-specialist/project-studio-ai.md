---
name: project-studio-ai
description: Studio/AI is a static editorial HTML/CSS site for an AI education school — no JS, no backend, no user input surfaces
metadata:
  type: project
---

Static site for an AI education school called Studio/AI. No JavaScript, no backend, no forms or user input surfaces.

**Why:** Coursera vibe-coding exercise using Claude Code. The CLAUDE.md workflow requires plan-first, minimal changes, and explicit security sign-off.

**How to apply:** Security concerns are limited to: external resource integrity (Google Fonts CDN — no SRI possible), external image CDN (picsum.photos — placeholder only), open `mailto:` links, and decorative `alt=""` images. No XSS/injection/auth surface exists. Focus review effort on accessibility, contrast, semantic HTML, and CSS maintainability.
