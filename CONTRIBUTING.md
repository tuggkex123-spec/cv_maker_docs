Contributing to CV Maker

This guide is for developers who change CV Maker. Read [About CV Maker](docs/concept.md) first for the design background.

## Before you start

1. Install the requirements and run the app, as the [README](README.md#install-and-run) describes.
2. Run the tests once: `npm test`. Confirm that they pass on your machine.

## Project layout

| Folder or file | Contents |
|---|---|
| `src/pages/` | Full pages, such as the editor |
| `src/components/` | Reusable interface parts and info pages |
| `src/ai/` | AI adapters, prompts, suggestion checks, file readers, and their tests |
| `src/hooks/` | Shared React hooks |
| `src/i18n/` | Interface translations |
| `src/utils/` | Helper functions |
| `src/testing/` | Shared test helpers |
| `src/App.jsx` | Page routes |
| `src/main.jsx` | Entry point |

Key files in `src/ai/`:

- `providers.js`: requests to OpenAI, Anthropic and Gemini, with retries and error handling
- `sanitize.js`: checks AI suggestions against the CV structure before the app applies them
- `session.js`: runs one turn of the assistant conversation
- `extractText.js`: reads PDF, Word and text files in the browser

## Commands

| Command | Purpose |
|---|---|
| `npm run dev` | Start the development server |
| `npm run build` | Build the production version |
| `npm run preview` | Preview the production build |
| `npm test` | Run the Node and Vitest suites |
| `npm run test:watch` | Run Vitest in watch mode |

Run `npm test` and `npm run build` before you open a pull request. Both must pass.

## Make a change

1. Create a branch from `main`. Use a short, descriptive name, such as `fix-pdf-import`.
2. Make small commits, each with one purpose.
3. Add or update a test for every behaviour change in `src/ai/`.
4. Update the documentation when a change affects what users do. Start with the [how-to guides](docs/how-to.md) and the [tutorial](docs/tutorial-first-cv.md).
5. Open a pull request. Describe the change, the reason for it, and how you tested it.

## Code style

- Keep functions short, and name them for what they do.
- Write comments that explain why, not what. The comments in `src/ai/providers.js` show the expected level of detail.
- Put all visible text in the translation files in `src/i18n/`, not in components.

## Before you change the AI code

- The app has no backend. A feature that calls an external service must run in the browser with the user's own key, or you must discuss the design first.
- Treat AI output as untrusted. Pass every model change through `sanitize.js` before the user sees it.
- Providers change their APIs and model names often. Check the provider's documentation before you change a request format.

## Questions

Open an issue to report a bug or to discuss a change before you start work.
