## Repo snapshot for AI coding agents

This is a small static UI clone of the HBO Max landing + sign-in pages (HTML + CSS only). The guidance below highlights the concrete, discoverable patterns and workflows an AI assistant should follow when editing or extending this codebase.

### Big picture

- No JS or backend: the project is pure HTML/CSS. Changes should be made by editing files under the repo root and `assets/`.
- Entry pages: `index.html` (landing) and `signIn.html` (login form).
- Styles: global variables and base rules live in `assets/global.css`; page-specific rules live in `assets/index.css` and `assets/signIn.css`.
- Images and static assets are under `assets/images/`.

### Architecture & patterns to follow

- CSS variable driven theme in `assets/global.css` (see `:root` variables). Prefer using these variables when adding colors/gradients.
- BEM-like class naming examples used throughout: `menu__item`, `header__title--light`, `subscription__card`. Preserve this pattern when adding selectors.
- Modifier classes follow `--` (e.g., `button--gradient`, `menu__item--button`). Use modifiers instead of new standalone classes when possible.
- Responsive behaviors: look at media queries in `assets/global.css` and page styles; follow existing breakpoints (480px, 800px, 1140px, 1200px).
- Modern CSS features used: `:has()` in `assets/index.css`, CSS custom properties, CSS animations/keyframes. Keep cross-browser compatibility in mind if adding new features.

### How to run and validate locally

- There is no build step. To preview pages serve the folder with a simple static server (recommended):

  python3 -m http.server 8000

- Open `http://localhost:8000/index.html` and `http://localhost:8000/signIn.html`.
- Note: many stylesheet links in HTML use absolute paths like `/assets/global.css`. Serve from repo root (as above) so absolute paths resolve correctly.

### Typical edits and examples

- Add a new section to the landing page: edit `index.html` and add CSS rules to `assets/index.css` using the existing `.container` and `.title` helpers.
- To change theme colors, update variables in `assets/global.css` `:root` rather than hard-coding colors.
- To add an image: put it in `assets/images/` and reference it with `assets/images/<name>`; prefer relative URLs (e.g., `assets/images/foo.png`) when editing HTML in the repo to keep paths consistent.

### What not to assume

- No JS/Node tooling, no package.json, no tests, and no build scripts are present. Don't add tooling without the user's request.
- Accessibility and i18n are not fully implemented; only make minimal, clearly scoped accessibility fixes unless asked.

### Files to reference when changing behavior

- `index.html` — main landing markup and BEM examples.
- `signIn.html` — login form structure and form-related classes (`.login__field`, `:invalid` rule in `signIn.css`).
- `assets/global.css` — theme tokens, base layout, buttons, nav and footer rules.
- `assets/index.css` — landing page visuals (gradients, cards, `:has()` interactions).
- `assets/signIn.css` — form visuals and validation styling.
- `README.md` — project intent, challenge/branch notes and image references.

If anything in these notes is unclear or you'd like more guidance (examples of a PR, or a suggested CSS snippet), tell me which part to expand and I'll iterate.
