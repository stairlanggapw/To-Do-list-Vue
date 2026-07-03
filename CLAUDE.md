# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- **Development server**: `npm run dev` – starts Vite dev server at http://localhost:5173.
- **Production build**: `npm run build` – creates optimized assets in `/dist`.
- **Preview production build**: `npm run preview` – serves the built app locally.
- **Linting**: No linting configuration is present yet. If you add ESLint, you can run `npm run lint` (add script to `package.json` as needed).
- **Testing**: No test runner is configured. You can add Vitest (`npm i -D vitest @vue/test-utils`) and then add a `test` script to run tests.

## High‑level Architecture

- **Bootstrap** – `src/main.js` creates the Vue application via `createApp(App).mount('#app')`.
- **Root component** – `src/App.vue` provides a full‑screen flex container that centers the `<TodoPage/>` component.
- **Feature component.
- **Styling** – Tailwind CSS is integrated via Vite plugin (`tailwindcss()` in `vite.config.js`). Utility classes are used directly in `.vue` files; there is no separate CSS framework.
- **State management** – The todo app uses Vue 3 Composition API with `ref()` for reactive state (`taskInput`, `tasks`). No external store (e.g., Pinia) is used.
- **Component structure** – All UI lives in `src/components/Todo-Page.vue`. Additional components should be placed under `src/components/` and imported where needed.
- **Assets** – Static assets (images, icons) belong in `public/` or `src/assets/` and are accessed via relative URLs or the `@` alias.
- **Build tool** – Vite with `@vitejs/plugin-vue` and `@tailwindcss/vite`. The config defines an alias `@` pointing to `src`.

### Typical workflow

1. Start the dev server: `npm run dev`.
2. Edit components under `src/components/`; changes hot‑reload.
3. When ready for production, run `npm run build` and inspect `dist/`.
4. Optionally preview the production build with `npm run preview`.

### Extending the project

- **Adding new features**: create a new `.vue` file in `src/components/` and import it where needed (e.g., in `App.vue` or another component).
- **Styling**: continue using Tailwind utility classes; if you need custom CSS, add it to `src/index.css` or a scoped `<style>` block in a component.
- **State sharing**: for larger apps, consider introducing Pinia; create a `src/stores/` folder and follow Pinia’s conventions.
- **Testing**: after adding Vitest, place test files alongside components (`*.spec.js`) or in a dedicated `tests/` folder; run with `npm test`.

This summary captures the essential project structure and common commands to help future instances of Claude Code become productive quickly.