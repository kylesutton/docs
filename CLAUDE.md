# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Mintlify documentation site. Pages are MDX files with YAML frontmatter; site configuration lives in `docs.json`.

## Common Commands

- **Local preview:** `mint dev` (serves at http://localhost:3000; requires Node.js 19+)
- **Custom port:** `mint dev --port 3333`
- **Validate links:** `mint broken-links`
- **Update CLI:** `npm mint update`
- **Install CLI:** `npm i -g mint`

## Architecture

### Configuration

- `docs.json` — Central config: navigation structure (tabs, groups, pages), theme colors, logos, navbar, footer, contextual options. Every content page must be registered here to appear in navigation.
- `.mintignore` — Files/dirs excluded from Mintlify builds (drafts/, *.draft.mdx, plus auto-ignored: .git, node_modules, README.md, etc.)

### Content Structure

- **Root pages:** `index.mdx`, `quickstart.mdx`, `development.mdx` — Getting started guides
- **`essentials/`** — Mintlify feature docs (settings, navigation, markdown, code, images, reusable-snippets)
- **`ai-tools/`** — AI tool integration guides (claude-code, cursor, windsurf)
- **`api-reference/`** — API documentation using OpenAPI spec (`openapi.json`) with thin MDX wrappers in `endpoint/` that reference endpoints via `openapi: 'METHOD /path'` frontmatter
- **`api/java/`** — Pre-built JavaDoc HTML for `com.gpudb.*` classes (not MDX; served as static content)
- **`snippets/`** — Reusable MDX fragments imported into other pages via `import ... from '/snippets/...'`
- **`images/`**, **`logo/`** — Static assets

### MDX Page Format

Every content page uses this structure:

```mdx
---
title: "Page Title"
description: "Brief description"
icon: "icon-name"  # optional
---

Page content with Mintlify components...
```

Key Mintlify components used: `<Card>`, `<CardGroup>`, `<Columns>`, `<Steps>/<Step>`, `<AccordionGroup>/<Accordion>`, `<Tip>`, `<Info>`, `<Warning>`, `<Note>`, `<CodeGroup>`, `<Frame>`, `<Latex>`.

### Navigation Model

`docs.json` defines two top-level tabs: **Guides** (Getting Started, Customization, Writing Content, AI Tools groups) and **API Reference** (API documentation, Endpoint examples groups). Pages are referenced by path without extension (e.g., `"essentials/settings"`).

## Writing Style

- Active voice, second person ("you")
- Sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references
- One idea per sentence
