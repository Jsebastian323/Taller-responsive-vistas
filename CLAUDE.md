# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**DevStudio** — a single-page responsive website workshop ("taller de vistas"). The site is a pure HTML/CSS project with no JavaScript and no build tools. Open `index.html` directly in a browser to preview.

## Architecture

### Single-page layout

All content lives in `index.html` as one page with anchor-based navigation (`#nosotros`, `#servicios`, `#portafolio`, `#contacto`). There is no JavaScript.

### CSS methodology: BEM

`styles.css` uses strict BEM naming (`block__element--modifier`). Key blocks:

| Block | Description |
|---|---|
| `.header` | Sticky top nav with brand and links |
| `.hero` | Full-width gradient banner with CTA |
| `.intro` | "Nosotros" section with tech-list card |
| `.services` | 3-column CSS Grid of service cards |
| `.portfolio` | 3×2 CSS Grid of colored portfolio cards |
| `.contact` | Centered form card |
| `.footer` | Dark footer matching the header |

The `.card` block is shared between services and portfolio, differentiated via `--service` and `--portfolio` / `--portfolio-N` modifiers.

### Layout utilities

- `.container`: `max-width: 1200px`, centered, `padding: 0 48px`
- Grids use `display: grid` with `repeat(3, 1fr)` for both services and portfolio
- No external CSS frameworks or preprocessors

### Color palette (indigo/dark theme)

| Token | Value |
|---|---|
| Primary indigo | `#4f46e5` |
| Dark navy (header/footer) | `#1a1a2e` |
| Light background | `#f8fafc` / `#f1f5f9` |
| Accent purple | `#7c3aed` |

## GitHub Actions (CI)

Two workflows in `.github/workflows/`:

- **`claude.yml`** — Claude PR Assistant: responds to `@claude` mentions in issues, PR comments, and reviews.
- **`claude-code-review.yml`** — Automatic code review on every pull request using the `code-review` plugin.

Both require the `CLAUDE_CODE_OAUTH_TOKEN` secret to be configured in the repository settings.

## Branching

- `main` — production branch
- `feature/desktop-layout` — active development branch (current)
