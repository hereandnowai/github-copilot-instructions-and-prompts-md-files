---
mode: agent
model: Claude Sonnet 4
description: "Deploy kids-gaming-site to GitHub & publish via GitHub Pages using GH CLI"
---

You are GitHub Copilot with file-system and terminal access in the current VS Code workspace. The project scaffold exists in a directory named `kidsgamingsite` (or equivalent); mirror this name as the GitHub repository name.

Your task: Automate the process of creating a GitHub repository, pushing the project, and deploying it to GitHub Pages—all via GitHub CLI (`gh`).

Steps to perform:

1. **Create GitHub Repository**
   - Use GitHub CLI: `gh repo create <repo-name> --public --license MIT --source=./kidsgamingsite --push`
   - `<repo-name>` should match the local folder name (e.g., `kidsgamingsite`).
   - Use `--source` to tell GH CLI to point to the local project folder.
   - Include `--push` to push current commits.

2. **Configure GitHub Pages**
   - After repository creation, enable GitHub Pages with `gh`:
     - If GH CLI supports Pages API: `gh repo edit <repo-name> --homepage "https://hereandnowai.github.io/<repo-name>"`
     - Alternatively, instruct in `README.md` to go to repository Settings → Pages → select `main` branch (root).

3. **Create a `.github/workflows/gh-pages.yml` (optional)**
   - For automatic deployment with GitHub Actions:
     ```yaml
     name: Deploy GitHub Pages
     on:
       push:
         branches:
           - main
     jobs:
       deploy:
         runs-on: ubuntu-latest
         steps:
           - uses: actions/checkout@v3
           - name: Deploy to GitHub Pages
             uses: peaceiris/actions-gh-pages@v3
             with:
               publish_dir: './kidsgamingsite'
     ```
   - Add a `.nojekyll` file to the project root to support static files.

4. **Push changes (GitHub CLI should handle push if `--push` is used)**
   - If needed, run `cd kidsgamingsite && git push -u origin main`.

5. **At the end, provide:**
   - `gh repo view <repo-name> --web` — to open the GitHub repo page.
   - A confirmation message:  
     ```
     Repository created and pushed:
     https://github.com/<your-username>/<repo-name>
     Site deployed at:
     https://hereandnowai.github.io/<repo-name> (allow a few minutes to go live)
     ```

---

Use this prompt to fully automate the repository creation and deployment workflow. Once copied as `.github/prompts/deploy.prompt.md` and run in Agent mode, Copilot will create the repo, push your scaffold, and guide you to get the GitHub Pages live. Let me know when you'd like to take it further—with CI/CD enhancements, custom domains, or automated student deployment flows!
::contentReference[oaicite:0]{index=0}
