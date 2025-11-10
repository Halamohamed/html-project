## Purpose

This file gives concise, actionable guidance for AI coding agents (and humans) to be productive in this tiny static HTML project.

## Big picture

- Project type: single-page static site. The main entry is `html-demo.html` in the repository root.
- Expected asset pattern: stylesheets and scripts live alongside the HTML (e.g. `styles.css`, `script.js`) and are referenced from the HTML using relative paths.
- There is no build system, package manager, or tests present in the repo. Treat changes as direct edits to files that will be served as static content.

## Files to know

- `html-demo.html` — primary file. Contains <meta> tags, a linked stylesheet (`styles.css`) and a deferred script (`script.js`). Use this file for page-level HTML changes.
- `styles.css` (may be absent) — expected CSS file in the same folder as the HTML.
- `script.js` (may be absent) — expected JS file loaded with `defer`. Prefer initializing behavior on load or via `DOMContentLoaded` if adding scripts.

## Developer workflows (discoverable / tested)

- Open for quick testing: open `html-demo.html` in the browser directly. In PowerShell you can run:

  ```powershell
  Invoke-Item .\html-demo.html
  ```

- Serve with a minimal static server (useful when loading modules or fetching relative assets):

  ```powershell
  python -m http.server 8000
  # then open http://localhost:8000/html-demo.html
  ```

- Do not introduce a package.json, bundler, or test harness without the user's explicit request — the repo is intentionally minimal.

## Agent guidance: what to do and what to avoid

- When editing HTML: keep changes localized to `html-demo.html` unless adding new assets. Preserve existing <meta> and <link>/<script> usage pattern.
- When adding JS: use `defer` or hook `DOMContentLoaded`. Example pattern (discoverable from existing HTML): `script.js` is referenced with `defer`.
- When adding CSS: keep it global in `styles.css` (no CSS-in-JS). Prefer simple BEM-like or kebab-case class names.
- No server-side code or APIs are present — avoid assumptions about backend integration.

## Integration points / external dependencies

- None are present in the codebase. If the task requires external services, clearly document the needed API keys and add integration points only after user approval.

## Small examples (inline guidance for code edits)

- Add a script file: create `script.js` and keep top-level initialization inside a `DOMContentLoaded` handler or export simple functions if later modularization is requested.
- Add a stylesheet: create `styles.css` and link it in `html-demo.html` (already present). Keep styling scope small and avoid frameworks.

## Constraints and assumptions (derived from repo)

- No build/test toolchain is present; assume manual or lightweight local workflows.
- Keep changes low-risk and reversible (single-file edits) unless the user asks for a larger refactor.

## Where to ask the user

- If a change requires adding a build tool, test runner, or external dependency, ask the user for approval and preferred tools.

---
Please review this guidance and tell me if you'd like more detail (preferred editor, browser targets, accessibility rules, or a sample `script.js`/`styles.css`).
