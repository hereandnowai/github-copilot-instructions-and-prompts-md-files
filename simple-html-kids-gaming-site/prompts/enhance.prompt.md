---
mode: agent
model: Claude Sonnet 4
description: "Enhance scaffold to functional branded site"
---

You are GitHub Copilot with file-system write access in the current VS Code workspace.

Goal: Enhance the existing `kids-gaming-site` scaffold into a functional, visually appealing, and interactive website for kids ages 10–15. Use data from:
- `data/branding.json`
- `data/theme.json`
- `data/games.json`

Tasks by file:

### index.html
- Add header with logo and nav.
- Hero section with tagline from `games.json`.
- Game list section populated via JS.
- Countdown timer using `games.json.countdownTarget`.
- Footer with contact from `branding.json.contact`.
- Accessible markup and `<!-- TODO: student exercise -->` markers.

### styles.css
- Apply CSS variables from `theme.json.colors` and `theme.json.font`.
- Cards, buttons, responsive design, focus states, comments for learners.

### scripts.js
- Load `branding.json`, `theme.json`, and `games.json`.
- Apply theme (colors, font).
- Populate logo, slogan, games, countdown, contact.
- Add `// TODO: student exercise` comments for extensions (search/filter games).

### games.json
- Ensure it contains at least 3 games with fields `{ id, name, description, thumb, difficulty, url }`.

### README.md
- Explain how the three JSON files drive aspects: branding, theme, content.
- Learning checkpoints reference `TODO` markers.

Operational steps:
- Overwrite the four files (index.html, styles.css, scripts.js, README.md).
- Output updated content in labeled code blocks.
- Print file tree and summary at end: “Enhancements applied.”

Proceed with enhancement now.
