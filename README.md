# Nuvve — European Power Market Brief (static demo)

A single-page static newsletter. **No build step, no dependencies** — just static files,
so it deploys to Vercel with zero configuration.

## Files
- `index.html` — the newsletter page. Fully self-contained: CSS and the SVG/JS-rendered
  charts are inline. Nothing else is required to render it.
- `vercel.json` — clean URLs + basic security headers (optional, safe to keep).
- `README.md` — this file.

## Deploy to Vercel

Pick whichever is easiest — all three give the same result.

### A. Drag & drop (fastest)
1. Go to **vercel.com → Add New… → Project**.
2. Drag this folder (or a zip of it) onto the upload area.
3. **Framework Preset: "Other".** Leave Build Command and Output Directory **blank**.
4. **Deploy.**

### B. Vercel CLI
```bash
npm i -g vercel
cd <this-folder>
vercel          # creates a preview URL
vercel --prod   # promotes to production
```
When prompted, accept the defaults — no build command, output directory `./`.

### C. Git import
Push these files to a GitHub repo, then **vercel.com → Import**. Framework Preset
**"Other"**, no build command.

## Local preview
```bash
npx serve .
# or
python3 -m http.server 8000
```
Then open http://localhost:8000

## Updating each issue
Open `index.html` and edit the fields/arrays marked `[[EDIT]]`. The data lives in a
`<script>` block near the bottom:
- `CHART_30D` — daily DK1 day-ahead prices (the June line chart)
- `HYDRO` — weekly Norwegian reservoir fill (the hydro chart)
- `SCENARIOS` + `REF_2025` — outlook bands and reference points (the fan chart)

The charts redraw automatically from those arrays — no other steps needed. Update the
prose, tables, masthead date, and "In brief" bullets in the marked sections.

## Notes
- Fonts load from Google Fonts (needs internet); the page falls back to system fonts offline.
- Charts are drawn client-side with inline SVG + a small script — no external chart library,
  no localStorage, no network calls beyond the font stylesheet.
