---
mode: 'agent'
model: Claude Sonnet 4
description: 'Generate and maintain Angular unit tests using Jasmine and Karma'
---

Your goal is to **create Jasmine unit tests for Angular 16+ apps that run with Karma**.  

### Requirements
- Follow Angular TestBed conventions:
  - Import `TestBed` from `@angular/core/testing`.
  - Use `beforeEach(async () => { ... })` with `TestBed.configureTestingModule`.
  - Always call `fixture.detectChanges()` after state changes.
- For component tests:
  - Verify initial DOM render.
  - Test user interactions (click, input).
  - Query DOM using `By.css()` from `@angular/platform-browser`.
- For service tests:
  - Use `HttpClientTestingModule` and `HttpTestingController` for HTTP requests.
  - Cover both success and error cases.
- Use `spyOn` for mocking dependencies.
- Ensure all tests are runnable with:
  ```bash
  ng test --no-watch --code-coverage
  ```
- Test names must be clear and behavior-driven (e.g., `it('should increment counter when increment() is called')`).

### Output format
- Return **only the .spec.ts file content** ready to be pasted.
- Do not include explanations or comments unless inside the code.
