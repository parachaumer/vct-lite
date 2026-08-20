# AliveDx VCT Lite (static)

Replit vct-lite UI, with the Excel-faithful vct-engine running in the browser.
No API server is required. This folder is the GitHub Pages artifact
(BASE_PATH=/vct-lite/ for repo parachaumer/vct-lite).

## Open this folder locally

Asset URLs are rooted at /vct-lite/, so serve a parent directory and name this
folder vct-lite:

    mkdir -p /tmp/vct-pages-root
    ln -sfn /workspace/vct-pages-dist /tmp/vct-pages-root/vct-lite
    python3 -m http.server 8766 --bind 0.0.0.0 --directory /tmp/vct-pages-root

Then open http://127.0.0.1:8766/vct-lite/

A same-UI preview built with BASE_PATH=/ is served at
http://127.0.0.1:8766/ (from /workspace/vct-static/dist-preview).

## Deploy to GitHub Pages (parachaumer/vct-lite)

1. Copy the contents of this folder (not the folder itself) to the gh-pages
   branch or /docs of https://github.com/parachaumer/vct-lite
2. Enable GitHub Pages for that source
3. Site: https://parachaumer.github.io/vct-lite/

404.html is a copy of index.html so /vct-lite/results/:id deep links work.
.nojekyll stops Jekyll from ignoring hashed assets.

## What this build does

- UI: unchanged Replit AliveDx design system (vct-lite + alivedx-ds).
- Formulas: vct-engine runLite / runAdvanced (config-driven disease
  split, marker ratios, instrument table — not hardcoded scenario numbers).
- Unlock: local only (sessionStorage). Reveals drivers D-F in this browser
  tab. No email is sent. Download PDF opens a print-friendly HTML page you
  can save as PDF.
- Assessments live in sessionStorage and disappear when the tab is closed.

## Rebuild

    cd /workspace/vct-static
    BASE_PATH=/vct-lite/ OUT_DIR=/workspace/vct-pages-dist bun run build

After a clean rebuild, recopy 404.html from index.html and touch .nojekyll
if the build emptied the folder.
