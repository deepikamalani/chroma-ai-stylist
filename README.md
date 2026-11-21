# CHROMA AI

A small personal styling studio with three steps: profile entry, skin-colour guidance, and category-aware wardrobe pairings.

## Run it

Open `index.html` in a browser to start at the overview. The sidebar links to the separate Colour Analysis, My Wardrobe, and Outfit Ideas pages. For a local development server, run this folder with any static server, for example:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Included

- Login/profile entry, skin-tone guidance, and wardrobe pages.
- Skin tone and undertone estimates with a small palette suggestion, confidence note, and manual adjustment.
- Clothing categories: tops, bottoms, one-pieces, shoes, outerwear, and accessories.
- Outfit rules pair a top with a bottom; one-pieces are styled separately. Optional missing-item suggestions appear when relevant.
- Wardrobe photos, dominant colour extraction, browser-local storage, edit-category and remove controls.
- GitHub Pages deployment workflow in `.github/workflows/deploy.yml`.
- Wardrobe images are resized and saved in IndexedDB (with a localStorage fallback and legacy migration); clearing site data removes them.
- Profile names and analysis completion are stored locally. This is a demo entry screen, not secure authentication; no password, remote database, or cross-device account is configured.

## Project structure

- `index.html` — studio overview
- `colour-analysis.html` — colour analysis page
- `wardrobe.html` — digital wardrobe page
- `outfits.html` — forwards to wardrobe pairings
- `styles.css` — shared responsive visual design and effects
- `app.js` — browser interactions and local image handling

## AI/ML project extension

The photo analysis currently runs locally in the browser. It samples the central image region, filters for skin-like pixels, then uses CIELAB lightness and colour differences to estimate Light/Medium/Deep tone and Warm/Neutral/Cool undertone. This is explainable image processing, not a trained AI model or validated skin-tone assessment. Lighting, makeup, camera processing, and backgrounds can change the estimate. For a research-grade AI/ML system, replace the heuristic with a validated model and controlled photo pipeline, report uncertainty, and test across skin tones and devices. Palette suggestions are a styling aid, and outfit ideas are colour-pairing suggestions rather than a fashion-trained recommender.

Uploaded clothing images are resized and saved in this browser's IndexedDB; clearing site data removes them. Selfies are previewed in memory and are not uploaded. Add a hosted authentication service, database, and image storage for secure accounts and cross-device sync.

## Publish with GitHub Pages

The workflow at `.github/workflows/deploy.yml` publishes the static site whenever a commit is pushed to `main`. Create a GitHub repository, push this folder to `main`, enable GitHub Pages with **GitHub Actions** as its source in repository settings, and wait for the workflow to finish. GitHub will show the public URL in the Pages settings and the workflow run.
