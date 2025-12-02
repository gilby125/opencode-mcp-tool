# Repository Guidelines

## Project Structure & Module Organization
- Source code lives in `src/` (entry point `src/index.ts`, tools in `src/tools/`, shared helpers in `src/utils/`, constants in `src/constants.ts`).
- Built artifacts are emitted to `dist/` and should not be edited by hand.
- Documentation is under `docs/` (guides, concepts, and usage examples) and static assets under `docs/public/`.

## Build, Test, and Development Commands
- `npm run build` – Compile TypeScript to JavaScript in `dist/` using `tsc`.
- `npm run dev` – Build once, then start the MCP server from `dist/index.js` for local development.
- `npm start` – Run the built MCP server (assumes `npm run build` has been run).
- `npm test` – Placeholder tests; currently prints a message and exits successfully.
- `npm run lint` – Type-check the project with `tsc --noEmit`.

## Coding Style & Naming Conventions
- Use TypeScript with ES modules and modern syntax (Node >= 16).
- Prefer explicit types and `zod` schemas for validation; keep tool definitions in `src/tools/` and shared logic in `src/utils/`.
- Use 2-space indentation, single quotes in TypeScript, and descriptive names for tools (e.g., `ask-opencode.tool.ts`).
- Do not edit files in `dist/`; change the corresponding `src/` file and rebuild.

## Testing Guidelines
- There is no formal test suite yet; add unit tests alongside new functionality where practical and keep them fast and deterministic.
- When adding tests, document how to run them (e.g., extend `npm test`) and keep any test helpers inside `src/utils/` or a dedicated `tests/` folder.

## Commit & Pull Request Guidelines
- Follow existing commit styles from `git log` (short, imperative subject lines such as `add new tool` or `fix timeout handling`).
- For pull requests, include a clear summary, mention affected files or tools (e.g., `src/tools/ask-opencode.tool.ts`), and link related issues.
- Add usage or behavior notes to `docs/` when introducing user-facing changes, and update the README if CLI behavior or configuration changes.
