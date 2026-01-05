# Repository Guidelines

## Project Structure & Module Organization

- `src/MMM-Linky.js` and `src/node_helper.js` are the MagicMirror module entry points.
- `src/components/` contains the core logic split by concern (API, parser, fetcher, chart, cache/files, timers).
- `MMM-Linky.css` holds module styles; `MMM-Linky.png` is the module image.
- `installer/` contains maintenance scripts used by npm tasks (setup, update, cache reset, minify).
- `data/` is used for cached API data generated at runtime.

## Build, Test, and Development Commands

- `npm run setup` initializes the module dependencies and assets (required after clone).
- `npm run update` pulls updates and rebuilds runtime assets.
- `npm run lint` runs ESLint across the repo.
- `npm run lint:fix` auto-fixes JS lint issues when possible.
- `npm run test` is alias for `npm run lint`.
- `npm run test:all` runs JS, CSS, and Markdown linting.
- `npm run reset:cache` clears cached API data in `data/` (use sparingly).

## Coding Style & Naming Conventions

- Indentation is 2 spaces with semicolons and double quotes (see `.eslint.config.mjs`).
- Keep module files in `src/` and component logic in `src/components/`.
- Prefer descriptive names like `fetcher`, `parser`, `node_helper` aligned with existing files.
- CSS is validated with Stylelint and Prettier settings from `.stylelintrc.json`.

## Testing Guidelines

- There are no unit tests; quality gates are linting commands.
- JS lint: `npm run lint`; CSS lint: `npm run test:css`; Markdown lint: `npm run test:markdown`.
- Keep Markdown formatting compatible with `markdownlint-cli2`.

## Commit & Pull Request Guidelines

- Commit messages are short and direct (examples: `fix: eslint warn`, `update version`, `v1.2.2`).
- PRs should describe the change, include any relevant screenshots for UI changes, and note config impacts.
- If you touch API behavior or caching, call out rate-limit considerations in the PR description.

## Configuration & Security Notes

- The module uses a personal Conso API token and a Linky PRM; never commit real credentials.
- Avoid frequent cache resets to respect API rate limits (see `npm run reset:cache`).
