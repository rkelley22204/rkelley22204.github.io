## Purpose
Help AI coding agents be immediately productive in this repository: a small static website built from the Start Bootstrap "Freelancer" theme.

## Quick project overview
- Type: Static site (HTML, CSS, JS). No Node/npm build or server-side code present.
- Key files:
  - `index.html` — single-page site markup built from the Freelancer theme (contains portfolio grid, modals, contact form).
  - `css/styles.css` — combined Bootstrap and theme CSS (large single file). Edit carefully; it contains both Bootstrap and custom theme rules.
  - `js/scripts.js` — thin custom script: navbar shrink, Bootstrap ScrollSpy activation, responsive collapse behavior.
  - `assets/` — images and favicon (portfolio images under `assets/img/portfolio/`).

## What to do first (how to preview/run)
- Local preview: open `index.html` in a browser or serve the folder with a simple HTTP server (useful for relative asset/CDN behavior). Example (PowerShell):

```powershell
# from repo root
python -m http.server 8000
# then open http://localhost:8000 in browser
```

## Project-specific patterns & conventions (useful examples)
- Portfolio items: each grid item in the portfolio section uses an inline image and a `data-bs-target` that opens a modal with a matching `id` (e.g. `data-bs-target="#portfolioModal1"` → modal `id="portfolioModal1"`). When adding items, add both the grid card and a corresponding modal block.
- Contact form: `form#contactForm` uses SB Forms. It contains `data-sb-form-api-token="API_TOKEN"` and the submit button is initially `class="btn btn-primary btn-xl disabled"`. To activate, replace the token with a real SB Forms token and remove the disabled class as per Start Bootstrap instructions.
- Scripts: `js/scripts.js` is intentionally minimal — avoid duplicating behavior already implemented there (navbar shrink, scrollspy, collapse on nav link click).
- CSS: `css/styles.css` contains Bootstrap variables and theme overrides — prefer small additions near the bottom if you must change theme colors, or add a separate small `css/custom.css` and include it after `styles.css` to reduce merge conflicts when upstreaming theme updates.

## Integration points & external dependencies
- CDN dependencies in `index.html`: Bootstrap bundle (JS) via jsDelivr, Font Awesome via CDN, Google Fonts. Editing these links is fine but note the project relies on the bundled Bootstrap JS for modals and scrollspy.
- SB Forms: the contact form requires an external SB Forms script (already included at the bottom). The form will not send without registering for an SB Forms API token.

## Helpful examples (copyable snippets)
- Add a portfolio tile (increment ID and match to modal `id`):

  1) Grid tile (place in `.row` inside `#portfolio`):

     ```html
     <div class="col-md-6 col-lg-4 mb-5">
       <div class="portfolio-item mx-auto" data-bs-toggle="modal" data-bs-target="#portfolioModal7">
         <div class="portfolio-item-caption d-flex align-items-center justify-content-center h-100 w-100">
           <div class="portfolio-item-caption-content text-center text-white"><i class="fas fa-plus fa-3x"></i></div>
         </div>
         <img class="img-fluid" src="assets/img/portfolio/new.png" alt="..." />
       </div>
     </div>
     ```

  2) Corresponding modal (add after existing modals):

     ```html
     <div class="portfolio-modal modal fade" id="portfolioModal7" tabindex="-1" aria-hidden="true">
       <div class="modal-dialog modal-xl">
         <div class="modal-content"> ... </div>
       </div>
     </div>
     ```

## Editing rules for AI agents
- Preserve paths and naming conventions (assets referenced as `assets/...`) — do not change to absolute filesystem paths.
- Keep Bootstrap JS and SB Forms script order: Bootstrap bundle first, then `js/scripts.js`, then SB Forms.
- When changing visual styles, prefer minimal diffs: either append small rules near the end of `css/styles.css` or add a new `css/custom.css` and include it after `styles.css` in `index.html`.
- For dynamic UI changes, check `js/scripts.js` first; mimic its style (vanilla JS, DOMContentLoaded handler, no module system).

## Verification & testing guidance
- Preview locally in a browser and manually test: navigation (scrollspy), modals (open/close), responsive navbar toggler, and contact form behavior (submit button disabled until you integrate SB Forms token).
- No automated tests or build steps present.

## If you need to change the theme or upgrade Bootstrap
- `css/styles.css` bundles Bootstrap and theme. If upgrading Bootstrap, prefer replacing the bundled CSS with a fresh upstream `styles.css` from Start Bootstrap and reapply small local overrides in a separate file to keep diffs small.

---
If anything in this file is unclear or you want additional examples (e.g. how to add a modal template or wire a new JS behavior), tell me which section to expand and I will iterate.
