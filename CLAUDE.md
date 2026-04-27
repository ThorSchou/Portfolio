# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Thor Schou's personal portfolio — a Hugo static site deployed to GitHub Pages at https://ThorSchou.github.io/Portfolio/. Content is Markdown, configuration is TOML, and an AI chatbot (Dify) is embedded in the footer and auto-synced with the portfolio content.

## Commands

```bash
# Local dev server
hugo server

# Production build (what CI uses)
hugo --minify --baseURL "https://ThorSchou.github.io/Portfolio/"
```

Hugo version: **0.147.0 extended**. The Blowfish theme is a git submodule — always use `--recurse-submodules` when cloning.

## Architecture

```
config/_default/   — All Hugo/theme config (TOML)
content/posts/     — Blog posts and portfolio articles (Markdown)
layouts/partials/  — Only extend-footer.html exists; embeds the Dify chatbot
themes/blowfish/   — Theme submodule (pinned to v2.101.0); do not edit
.github/workflows/ — Two CI pipelines (deploy + Dify sync)
```

**Config files and their roles:**
- `config/_default/hugo.toml` — theme, baseURL, taxonomies, analytics hooks
- `config/_default/params.toml` — appearance, author info, feature toggles
- `config/_default/languages.en.toml` — language and date format
- `config/_default/menus.en.toml` — navigation items
- `config/_default/markup.toml` — Goldmark, LaTeX, code highlighting, TOC

## Deployment & CI

Two GitHub Actions workflows trigger on push to `main`:

1. **hugo.yml** — Builds with `hugo --minify` and deploys `public/` to GitHub Pages. Requires submodule checkout.
2. **sync-dify.yml** — Fires when files in `content/` change. Re-uploads all `.md` files (except `_index.md`) to the Dify dataset (`14db97c1-ade2-40e4-8600-04c12b622122`), deleting old versions first to prevent duplicates. Uses secret `DIFY_API_KEY`.

`public/` is git-ignored and generated at build time.

## Dify Chatbot

The RAG chatbot is embedded via `layouts/partials/extend-footer.html`. It uses Dify's JS embed with token `mjzmELvnn65Xu0id`. Any new content in `content/posts/` is automatically synced to the Dify knowledge base on push, keeping the chatbot current.

## Adding Content

Use Hugo frontmatter with `title`, `date`, `categories`, `tags`, and optionally `canonicalURL`. New posts go in `content/posts/`. The sync workflow will pick them up automatically — no manual Dify steps needed.
