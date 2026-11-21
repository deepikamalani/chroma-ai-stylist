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
- First-visit local profile gate, then a separate colour-analysis flow.
- Skin-tone result is shown as Light, Medium, or Deep with a separate Warm, Neutral, or Cool undertone estimate; sample profiles are clearly marked.
- Colour palette suggestions are a styling aid derived from the skin-tone estimate, not the analysis result itself.
- Wardrobe photo uploads, dominant image colour sampling, browser-local persistence, and remove controls.
- Photo estimates use central skin-like pixels and CIELAB lightness/colour differences for a tentative skin tone and undertone. Low-signal images show guidance instead of receiving a random result. Users can manually refine tone and undertone or explore labelled sample profiles.
- Wardrobe photos are resized before saving, and colour sampling de-emphasizes blank white backgrounds.
- Outfit combination cards populated from wardrobe items, with a mix-it-up animation.
- Floating and animated graphics with reduced-motion support.
- GitHub Pages deployment workflow in `.github/workflows/deploy.yml`.
- Wardrobe images are resized and saved in IndexedDB (with a localStorage fallback and legacy migration); clearing site data removes them.
- Profile names and analysis completion are stored locally. This is a demo entry screen, not secure authentication; no password, remote database, or cross-device account is configured.

## Project structure

- `index.html` — studio overview
- `colour-analysis.html` — colour analysis page
- `wardrobe.html` — digital wardrobe page
- `outfits.html` — outfit ideas page
- `styles.css` — shared responsive visual design and effects
- `app.js` — browser interactions and local image handling

## AI/ML project extension

The photo analysis currently runs locally in the browser. It samples the central image region, filters for skin-like pixels, then uses CIELAB lightness and colour differences to estimate Light/Medium/Deep tone and Warm/Neutral/Cool undertone. This is explainable image processing, not a trained AI model or validated skin-tone assessment. Lighting, makeup, camera processing, and backgrounds can change the estimate. For a research-grade AI/ML system, replace the heuristic with a validated model and controlled photo pipeline, report uncertainty, and test across skin tones and devices. Palette suggestions are a styling aid, and outfit ideas are colour-pairing suggestions rather than a fashion-trained recommender.

Uploaded clothing images are resized and saved in this browser's IndexedDB; clearing site data removes them. Selfies are previewed in memory and are not uploaded. Add a hosted authentication service, database, and image storage for secure accounts and cross-device sync.

## Publish with GitHub Pages

The workflow at `.github/workflows/deploy.yml` publishes the static site whenever a commit is pushed to `main`. Create a GitHub repository, push this folder to `main`, enable GitHub Pages with **GitHub Actions** as its source in repository settings, and wait for the workflow to finish. GitHub will show the public URL in the Pages settings and the workflow run.
