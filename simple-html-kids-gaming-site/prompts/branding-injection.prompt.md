---
mode: agent
model: Claude Sonnet 4
description: "Inject organizational branding from branding.json into scaffold"
---

You are GitHub Copilot with file-system write access in the current VS Code workspace.

Precondition: `data/branding.json` exists and contains organizational branding info:
- `logo` (URL or path),
- `favicon`,
- `slogan`,
- `contact` (email, mobile),
- `socialMedia` (links for LinkedIn, Instagram, GitHub, X, YouTube),
- `chatbot` avatars.

Your task: Integrate this branding into scaffold files (`index.html`, `styles.css`, `scripts.js`, `README.md`).

Requirements:

### index.html
- Add `<link rel="icon">` for `branding.json.favicon`.
- Inject logo image in header.
- Display slogan in hero.
- Render social icons/links.
- Include contact info in footer with semantic markup.

### styles.css
- Use CSS variables from `branding.json.theme.colors`.
- Load font from `branding.json.theme.font`.

### scripts.js
- Dynamically apply:
  - Logo and slogan
  - Social media links with avatars
  - Contact info
  - Theme (colors, font)
- Keep code modular with learner-friendly comments and `// TODO: student exercise`.

### README.md
- Document how `branding.json` drives site branding.
- Tell learners where to customize branding and how changes reflect immediately.
- Include learning checkpoints.

Operational steps:
- Overwrite or update target files.
- Provide full file content in labeled code blocks.
- Print a file tree snapshot and success summary at end.

Generate the branding-injected updates now.
