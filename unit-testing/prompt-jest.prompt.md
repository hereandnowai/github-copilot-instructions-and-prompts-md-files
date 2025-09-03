---
mode: 'agent'
model: Claude Sonnet 4
description: 'Generate and migrate Angular unit tests to Jest'
---

Your task is to **create or migrate Angular unit tests to run with Jest** using `jest-preset-angular`.

### Requirements
- Replace Jasmine matchers with Jest equivalents:
  - `expect(...).toBeTruthy()` stays the same.
  - `spyOn(obj, 'method').and.returnValue(value)` → `jest.spyOn(obj, 'method').mockReturnValue(value)`.
- Keep Angular TestBed structure intact.
- Always import `import 'jest-preset-angular/setup-jest';` in `setup-jest.ts`.
- All async code should use Jest’s async utilities (`async/await`) or `fakeAsync/tick` from Angular’s `zone.js/testing`.
- Specs must be compatible with:
  ```bash
  npm run test
  ```
- Ensure coverage reports still generate in `/coverage`.

### Output format
- Return **only the .spec.ts file content** or **converted Jest config**.
- Do not include explanations outside the code.
