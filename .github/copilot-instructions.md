# Copilot instructions

Project context Copilot should apply to every session in this repository.

## Stack

- Framework: Astro (static output).
- Language: TypeScript.
- Styling: plain CSS in the base layout.

## Conventions

- Keep components small and focused.
- Prefer semantic HTML and accessible markup.
- Do not close, or add closing keywords for, the exercise walkthrough issue (issue #1) in any pull request. The exercise's GitHub Actions workflows manage that issue. When you open a pull request for app work, link only the specific app work-item issue you are implementing.

## Persistence and hydration rules

- **Persistence**: bookmarks are stored in the browser with `localStorage` under a single key, as a JSON array of `{ url, slug }` objects. There is no backend, so never send bookmark data to a server. Wrap reads in `try`/`catch` and fall back to an empty list when stored data is missing or invalid.
- **Hydration**: browser-only code (`localStorage`, `document`, `window`, `navigator.clipboard`) must run only on the client, never in component frontmatter or at build time. Keep it in the component's client `<script>` block. If a bookmarks UI is ever built as a framework component, mount it with the `client:load` directive so it hydrates in the browser and the static build never touches browser APIs.
