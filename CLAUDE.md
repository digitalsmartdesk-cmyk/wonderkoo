# WonderKoo Stories — Site Handoff

## Site identity
- **Name**: WonderKoo Stories
- **Series**: 55 picture books · 7 seasons · Indians who amazed the world
- **Live artifact**: https://claude.ai/artifact/DpVkotznafTUWyKuVFWp2R (Version 3)
- **Contact email**: wonderkoo@quizykoo.com

## File structure
```
index.html              ← single-page source, matches live artifact
img/
  wonderkoo-logo.png    ← WonderKoo logo
  s1-b1.jpg             ← Season 1 book covers (s<season>-b<book>.jpg)
  s1-b2.jpg
  ...
  s7-b8.jpg             ← Season 7, book 8
  s1-teaser.jpg         ← Season teaser/hero images
  s2-teaser.jpg
  ...
  s7-teaser.jpg
```

## Seasons (7 seasons, 55 books total)
| Season | Theme | Books |
|--------|-------|-------|
| Season 1 | Pioneers | 8 |
| Season 2 | Visionaries | 8 |
| Season 3 | Trailblazers | 8 |
| Season 4 | Innovators | 8 |
| Season 5 | Champions | 8 |
| Season 6 | Guardians | 8 |
| Season 7 | Legends | 7 |

## Design tokens
- **Theme**: Navy / sun-yellow — bold, celebratory, child-friendly
- **Fonts**: Fredoka (headings, Google Fonts) + Lora (body)
- **Navy**: `#1a2744` · Yellow accent: `#f5c842`
- Light-mode committed (single theme, no dark variant)

## Site structure
The page is a single-page app with JS-rendered views:
- **Home view**: Hero, signup form, season grid, about section, footer
- **Season pages**: Dynamically rendered per season with book grid

Navigation is hash-based (`#home`, `#season-1` through `#season-7`).

## Book data
All book and season metadata is in the `SEASONS` const array in the `<script>` block.
Each season: `{ id, name, tagline, teaser, books: [{title, cover, link}] }`
- `teaser` → `img/s<n>-teaser.jpg`
- `cover` → `img/s<n>-b<n>.jpg`

## Live Amazon links
⚠️ **Only Season 1 books (s1-b1 through s1-b4) have live Amazon links.**
All other book links are placeholder `#` links. Update the `link` field in the SEASONS array when books go live.

## Signup form note
The email signup form uses `window.claude.use('db')` for storing emails.
The artifact is published with `capabilities: {db: {rules: [...]}, user: {}}` declared (Version 4).
Signups are stored in `signups/<uid>` with `{email, interests, updated}`.
Only the owner can list all signups; each user reads/writes their own doc.
The `config/buy` doc (collection `config`) overrides buy links at runtime — set it via ArtifactData to add new Amazon links without republishing.

## To update and publish via Claude Code
```
# Open in Claude Code, then in Claude:
# 1. Edit index.html (update Amazon links, add new books, text, etc.)
# 2. Tell Claude: "Publish this to https://claude.ai/artifact/DpVkotznafTUWyKuVFWp2R"
```

## Footer / Contact
Email appears in the footer small-print as a mailto link: `wonderkoo@quizykoo.com`
