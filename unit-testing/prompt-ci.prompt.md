---
mode: 'agent'
model: Claude Sonnet 4
description: 'Generate CI workflows to run Angular unit tests with both Karma and Jest'
---

You are helping configure **GitHub Actions workflows** to run Angular unit tests automatically on push/PR.

### Requirements
- Workflow must:
  - Run on `ubuntu-latest`.
  - Use `actions/checkout` and `actions/setup-node`.
  - Cache `node_modules`.
  - Install dependencies with `npm ci`.
  - Run tests in both environments:
    - Karma (Angular default): `ng test --no-watch --code-coverage`
    - Jest: `npm run test`
  - Upload coverage reports as workflow artifacts.
- Add matrix for Node.js versions `[18.x, 20.x]`.

### Output format
- Return only `.github/workflows/ci.yml` content.
- Do not include explanations outside YAML.
