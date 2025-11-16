# Contributing to SpeakSphere

First off, thank you for considering contributing to SpeakSphere! It's people like you that make open source such a great community.

## Code of Conduct

This project and everyone participating in it is governed by a [Code of Conduct](./CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

## How Can I Contribute?

- **Reporting Bugs**: If you find a bug, please open an issue and provide as much detail as possible, including steps to reproduce it.
- **Suggesting Enhancements**: If you have an idea for a new feature or an improvement, open an issue to discuss it.
- **Pull Requests**: If you have a bug fix or a new feature ready, you can submit a pull request.

## Pull Request Process

1.  **Fork the repository** and create your branch from `main` (or `develop` for new features not yet in production).
2.  **Name your branch** descriptively, e.g., `feat/add-appointment-reminders` or `fix/chat-api-validation`.
3.  **Add your code**. Ensure your code adheres to the project's style guidelines.
4.  **Add or update tests** to cover your changes. Untested features or fixes will not be merged.
5.  **Update the documentation** (`README.md`, `API_DOCS.md`, etc.) if your changes affect it.
6.  **Ensure all tests pass** by running the test suite locally.
7.  **Submit the pull request**. Provide a clear title and a detailed description of your changes. Link to any relevant issues.

## Coding Style

### Documenting API Changes

If your contribution adds or modifies an API endpoint, you must update the `docs/API_DOCS.md` file. The documentation for each endpoint should include:

- The HTTP method and endpoint path (e.g., `POST /chat`).
- A clear description of the endpoint's purpose.
- A detailed breakdown of the request body, including fields, types, and whether they are required.
- Examples of success and error responses.
- A list of possible non-200 status codes and their meanings.

### Python (Backend)

- We follow the **PEP 8** style guide.
- Use `black` for code formatting and `flake8` for linting.
- Docstrings should follow the Google Python Style Guide.

### JavaScript/TypeScript (Frontend)

- We use **Prettier** for code formatting.
- Follow the Airbnb JavaScript Style Guide.

### Git Commit Messages

We follow the Conventional Commits specification. This helps in automating changelogs and makes the commit history more readable.

Examples:

- `feat: allow users to rate chatbot responses`
- `fix: correct time zone handling in appointment scheduler`
- `docs: update API documentation for the chat service`
- `style: format python code with black`
- `refactor: simplify conversation history retrieval`
- `test: add unit tests for inventory low-stock alerts`

Thank you for your contribution!
