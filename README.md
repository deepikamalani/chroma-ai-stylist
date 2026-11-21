# CHROMA AI

A responsive, multi-page personal colour and wardrobe styling studio. It runs directly in a modern browser and does not need a package install or build step.

## Run it

Open `index.html` in a browser to start at the overview. The sidebar links to the separate Colour Analysis, My Wardrobe, and Outfit Ideas pages. For a local development server, run this folder with any static server, for example:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Included

- Responsive studio overview and dedicated Colour Analysis, My Wardrobe, and Outfit Ideas pages.
- Clear colour-profile results with labelled palette swatches, click-to-copy colour values, and styling notes.
- Local selfie preview and sample profile.
- Wardrobe photo uploads, dominant image colour sampling, browser-local persistence, and remove controls.
- Photo-based colour estimates can vary between Light Spring, Soft Summer, Warm Autumn, and Clear Winter instead of always returning one palette. Optional undertone and depth controls let users refine the estimate.
- Wardrobe photos are resized before saving, and colour sampling de-emphasizes blank white backgrounds.
- Outfit combination cards populated from wardrobe items, with a mix-it-up animation.
- Floating and animated graphics with reduced-motion support.
- GitHub Pages deployment workflow in `.github/workflows/deploy.yml`.
- No database or account service is needed for this privacy-first prototype; each visitor's wardrobe stays in their own browser.

## Project structure

- `index.html` — studio overview
- `colour-analysis.html` — colour analysis page
- `wardrobe.html` — digital wardrobe page
- `outfits.html` — outfit ideas page
- `styles.css` — shared responsive visual design and effects
- `app.js` — browser interactions and local image handling

## AI/ML project extension

The photo analysis currently runs locally in the browser. It samples the central image region, filters for skin-like pixels, then applies a simple colour-temperature and lightness heuristic to choose a seasonal starting palette. This is explainable image processing, not a trained AI model or validated skin-tone assessment. Lighting, makeup, camera processing, and backgrounds can change the estimate. For a research-grade AI/ML system, replace the heuristic with a validated model and controlled photo pipeline, report uncertainty, and test across skin tones and devices. Clothing colour extraction uses a small image canvas; outfit ideas are colour-pairing suggestions rather than a fashion-trained recommender.

Uploaded clothing images are resized and saved in this browser's `localStorage`; clearing site data removes them. Selfies are previewed in memory and are not uploaded. Add an account system, database, and image storage only if cross-device sync or shared user profiles become requirements.

## Publish with GitHub Pages

The workflow at `.github/workflows/deploy.yml` publishes the static site whenever a commit is pushed to `main`. Create a GitHub repository, push this folder to `main`, enable GitHub Pages with **GitHub Actions** as its source in repository settings, and wait for the workflow to finish. GitHub will show the public URL in the Pages settings and the workflow run.
