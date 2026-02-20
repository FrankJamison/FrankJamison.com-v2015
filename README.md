# FrankJamison.com v2015

Static portfolio site (2015) built with plain HTML/CSS/JS (Bootstrap + jQuery). No build step.

## URLs

- Live preview: https://frankjamison2015.fcjamison.com/
- Local vhost (this workspace’s VS Code task): http://frankjamisoncomv2015.localhost/

If your local vhost uses a different hostname, update the URL in `.vscode/tasks.json` (task: **Open in Browser**).

### Localhost URL note

Older docs for this repo referenced `http://2015frankjamison.localhost/`. The current VS Code task and expected local vhost URL is `http://frankjamisoncomv2015.localhost/`.

## Quick start (local)

### Option A: VS Code task (vhost)

Run the VS Code task:

- **Open in Browser** (starts Chrome at `http://frankjamisoncomv2015.localhost/`)

### Option B: any static server

Serving files (rather than opening `index.html` via `file://`) avoids browser restrictions.

- Python 3: `python -m http.server 8000`
- Node: `npx serve .`

Then open `http://127.0.0.1:8000/` (or whatever URL your server prints).

## What changed recently

- HTML page title set to `FrankJamison.com v2015` in `index.html`.
- README updated to use the current localhost URL (`frankjamisoncomv2015.localhost`) and to include the live preview URL.

## Tech stack

- **HTML:** `index.html` (single entry point)
- **CSS:** Bootstrap + Normalize + custom styling + optional color skins
- **JavaScript:** jQuery + Bootstrap JS + a small set of site scripts
- **Assets:** images + icon fonts

## Project anatomy (where to change what)

- `index.html` — single entry point; all sections and content live here.
- `css/` — styling stack
  - `bootstrap.min.css` — responsive grid + baseline components.
  - `normalize.css` — cross-browser normalization.
  - `font-awesome.min.css`, `linecons.css` — icon sets.
  - `style.css` — primary site styling and overrides.
  - `colors/` — theme “skins” (e.g. `blue.css`, `green.css`, etc.).
- `js/` — runtime behavior
  - `jquery.min.js` — dependency for legacy interactions.
  - `bootstrap.min.js` — Bootstrap JS components.
  - `main.js`, `layout.js`, `default.js`, `watch.js` — site-specific behaviors (menu/scroll/layout/etc.).
- `images/` — site imagery
  - `portfolio/`, `team/`, `gmaps/` — grouped assets used by sections.
- `fonts/` — icon font assets referenced by CSS.
- `Frank Jamison.vcf` — downloadable vCard.

## Design & theming notes

### Layout + responsive behavior

The page is structured around Bootstrap’s grid. When editing markup in `index.html`:

- Prefer Bootstrap container/row/column patterns for consistent responsive behavior.
- Keep section blocks semantically grouped (one wrapper per section) to preserve spacing rules defined in `css/style.css`.

### Color theming (skins)

Theme color is controlled by a single stylesheet under `css/colors/`.

- To change the site’s accent palette, switch which `css/colors/*.css` file is linked in `index.html`.
- Keep “base” styling in `css/style.css`; keep palette-only changes in the chosen skin file.

### Icons + typography

Two icon sets are present:

- Font Awesome (`css/font-awesome.min.css`)
- Linecons (`css/linecons.css`)

When adding icons, stick to the existing set already used in the page so the visual weight stays consistent.

### Imagery

Images are referenced with relative paths from `index.html`.

Good practice when adding/replacing images:

- Prefer consistent aspect ratios within a section (especially portfolio grids).
- Optimize file sizes (JPEG/PNG compression) to avoid slowing down initial load.

## JavaScript behavior notes

The codebase is intentionally “classic” front-end:

- Scripts are global and rely on jQuery.
- Load order matters: keep `jquery.min.js` before scripts that depend on it.

If you introduce new behavior, aim to:

- Keep changes localized to one site script (avoid scattering across multiple files).
- Avoid adding new dependencies unless necessary (this is a no-build static site).

## Common changes (fast paths)

- **Edit content/sections:** update `index.html`.
- **Swap theme color:** change the linked file under `css/colors/` in `index.html`.
- **Adjust spacing/typography:** update `css/style.css` (prefer overrides there vs editing vendor CSS).
- **Update contact card:** edit `Frank Jamison.vcf`.

## Deployment

Deploy by copying the repository contents to any static host or web server (IIS/Apache/Nginx).

Checklist:

- `index.html` is at the site root.
- `css/`, `js/`, `images/`, `fonts/` remain alongside it (relative paths intact).
- Verify fonts/icons load (broken font paths are the most common post-deploy issue).

## Review checklist (for quick QA)

- Check the page at multiple viewport widths (mobile/tablet/desktop) to confirm grid behavior.
- Verify that portfolio/team images resolve and are reasonably optimized.
- Confirm icon fonts render (Font Awesome + Linecons).
- If a color skin is enabled, verify contrast/readability across key sections.
