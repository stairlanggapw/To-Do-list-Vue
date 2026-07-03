# To-Do Vue App

A simple yet feature‑rich **To‑Do list** application built with **Vue 3**, **Vite**, and **Tailwind CSS**. The app demonstrates core Vue concepts such as the Composition API, reactive state with `ref()`, event handling, conditional rendering, and list rendering, all styled with utility‑first CSS.

---

## 📋 Table of Contents
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Folder Structure](#folder-structure)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Styling](#styling)
- [State Management](#state-management)
- [Extending the Project](#extending-the-project)
- [License](#license)

---

## 🖥️ Overview
The application lets users:
- Add new to‑do items via an input field (Enter key or **+** button).
- Mark items as complete/incomplete with a check‑icon toggle.
- Delete items with a trash‑icon button.
- View static category chips (To‑Do / Progress / Done) for visual grouping.
- See an empty‑state message when the list is empty.
- Enjoy a responsive, centered card layout powered by Tailwind’s flex utilities.

---

## 🛠️ Tech Stack
| Category | Tool/Library | Version (as of `package.json`) |
|----------|--------------|--------------------------------|
| Framework | Vue 3 | ^3.5.38 |
| Build Tool | Vite | ^8.0.16 |
| Vue Plugin | @vitejs/plugin-vue | ^6.0.7 |
| CSS Framework | Tailwind CSS (via Vite plugin) | ^4.3.2 |
| Icons | lucide-vue-next | ^1.0.0 |
| DevTools | vite-plugin-vue-devtools | ^8.1.2 |

---

## 🗂️ Folder Structure
```
to-do-vue/
├─ public/                 # Static assets (favicon.ico)
│   └─ favicon.ico
├─ src/
│   ├─ assets/             # (empty) – place images, fonts, etc.
│   ├─ components/
│   │   └─ Todo-Page.vue   # Main UI component – holds all app logic
│   ├─ App.vue             # Root component – centers TodoPage in a flex container
│   ├─ main.js             # Vue entry point – creates app and mounts to #app
│   └─ index.css           # Global CSS (currently empty, can be used for custom styles)
├─ .git/
├─ .vscode/                # VS Code settings (optional)
├─ .gitignore
├─ index.html              # HTML template with <div id="app"></div>
├─ jsconfig.json           # VS Code/JavaScript path mapping (alias @ → /src)
├─ package-lock.json
├─ package.json            # npm scripts and dependencies
└─ vite.config.js          # Vite config – Tailwind & Vue plugins, alias @
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** (≥22.18.0 or ≥24.12.0 as defined in `package.json` engines)
- **npm** (comes with Node) or **yarn** / **pnpm** if preferred.

### Installation
```bash
# Clone the repository (if you haven't already)
git clone <repository-url>
cd to-do-vue

# Install dependencies
npm install
```

### Development Server
```bash
npm run dev
```
- Starts Vite dev server at **http://localhost:5173** (default).
- Hot Module Replacement (HMR) enables instant UI updates on file changes.

### Production Build
```bash
npm run build
```
- Generates optimized static assets in the `/dist` folder.

### Preview Production Build
```bash
npm run preview
```
- Serves the built app locally from `/dist` for final verification.

---

## 📦 Available Scripts (from `package.json`)
| Script | Description |
|--------|-------------|
| `dev` | Launch Vite development server (`vite`). |
| `build` | Create a production‑ready build (`vite build`). |
| `preview` | Preview the production build (`vite preview`). |

*Feel free to add additional scripts (e.g., `lint`, `test`) as the project evolves.*

---

## 🎨 Styling
- **Tailwind CSS** is integrated via the Vite plugin (`@tailwindcss/vite`). All styling is done with utility classes directly in `.vue` files.
- Global CSS can be added to `src/index.css` (imported in `main.js`).
- Component‑scoped styles belong inside `<style scoped>` blocks in `.vue` files.
- Icons are sourced from **lucide-vue-next** and imported as needed.

---

## 💾 State Management
- The app uses Vue 3’s **Composition API** with `ref()` for reactive state:
  - `taskInput`: bound to the text field (`v-model`).
  - `tasks`: an array of task objects (`{ id, title, completed }`).
- Mutations to these refs trigger automatic DOM updates.
- No external store (e.g., Pinia) is used; for larger applications consider migrating to Pinia and placing stores under `src/stores/`.

---

## 🔧 Extending the Project
1. **New Components**  
   Create `.vue` files in `src/components/` and import them where needed (e.g., in `App.vue` or another component).
2. **Routing**  
   If navigation is required, add `vue-router` (`npm i vue-router`) and define routes in `src/router/index.js`.
3. **State Sharing**  
   For global state, adopt **Pinia**: create a `src/stores/` folder and follow Pinia’s module pattern.
4. **Testing**  
   Add Vitest (`npm i -D vitest @vue/test-utils`) and a `test` script (`"test": "vitest"`). Place test files alongside components (`*.spec.js`) or in a `tests/` directory.
5. **Linting / Formatting**  
   Add ESLint & Prettier (`npm i -D eslint prettier eslint-plugin-vue eslint-config-prettier`) and configure lint scripts.

---

## 📄 License
This project is open source and available under the **MIT License** – see the `LICENSE` file for details (if you add one).

---

**Happy coding!** 🎉