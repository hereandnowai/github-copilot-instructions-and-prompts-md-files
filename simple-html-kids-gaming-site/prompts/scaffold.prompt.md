---
mode: agent
model: Claude Sonnet 4
description: "Create scaffold for kids-gaming-site project"
---

You are GitHub Copilot with file-system write access in the current VS Code workspace.

Goal: Create a complete project scaffold named `kids-gaming-site` inside the current workspace root.

Please create the following files and directories with full initial content:

- `kids-gaming-site/index.html`
- `kids-gaming-site/styles.css`
- `kids-gaming-site/scripts.js`
- `kids-gaming-site/data/branding.json`
- `kids-gaming-site/data/theme.json`
- `kids-gaming-site/data/games.json`
- `kids-gaming-site/README.md`
- `kids-gaming-site/.gitignore`
- `kids-gaming-site/assets/images/.gitkeep`
- `kids-gaming-site/assets/icons/.gitkeep`

Requirements:
- Use mobile-first design, semantic HTML5, ARIA roles and labels, and clear learner-friendly comments (`TODO: student exercise`).
- Ensure visually pleasing UI for ages 10–15 (rounded UI, large tap targets, bright but tasteful colors).
- `index.html` must link CSS and JS files.
- `styles.css`: define base styles with CSS variables (`--primary`, `--accent`, `--bg`, `--text`), responsive grid, and focus states.
- `scripts.js`: must fetch JSON files (branding, theme, games), populate DOM, and include comments for student work.
- `branding.json`: include logo, slogan, contact, and social media placeholders.
- `theme.json`: include color palette and font default.
- `games.json`: include site title, tagline, countdown, and at least 2 sample games.
- `README.md`: contain setup instructions, summary of project, and TODO learning prompts.
- `.gitignore`: ignore `.vscode`, `node_modules/`, `.DS_Store`.

Operational steps:
1. If `kids-gaming-site` exists, overwrite listed files.
2. If creation is not possible, output full content for each file in labeled code blocks.
3. After file creation, run:
Print `git status` and file tree.
4. End with success summary and `code kids-gaming-site` command.

Please generate this scaffold now.
1. Check if `kids-gaming-site` directory exists. If it does, overwrite the specified files. If not, create the directory and files.
2. Create or overwrite the following files with initial content:
   - `index.html`
   - `styles.css`
   - `scripts.js`
   - `data/branding.json`
   - `data/theme.json`
   - `data/games.json`
   - `README.md`
   - `.gitignore`
   - `assets/images/.gitkeep`
   - `assets/icons/.gitkeep`
3. Print `git status` and file tree.
4. End with success summary and `code kids-gaming-site` command.