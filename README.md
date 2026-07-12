# Bloom — landing page

Single-page, static landing page for Bloom (an open motion-system project). No build step — it's one self-contained `index.html`.

## Structure

```
.
├── index.html          # the whole page (HTML + CSS + JS inline)
├── assets/
│   └── hero.jpg         # background photo for the right panel (add this)
└── README.md
```

## Before you deploy

The hero image currently points at a local path on one machine
(`file:///C:/Users/.../pexels-jessef11-732548.jpg`), which will **not**
load once this is hosted anywhere else. To fix it:

1. Create an `assets/` folder in the repo.
2. Add your image there, e.g. `assets/hero.jpg`.
3. In `index.html`, find the `.hero-image` rule and change the `url(...)` to:
   ```css
   background: var(--placeholder-bg) url('assets/hero.jpg') center center / cover no-repeat;
   ```

## Deploying with GitHub Pages

1. Create a new GitHub repo (public, unless you have Pages on a paid plan).
2. Push this folder to it:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Bloom landing page"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main**, folder: **/ (root)**
   - Save.
4. GitHub will publish it at:
   `https://<your-username>.github.io/<repo-name>/`
   (First deploy can take a minute or two.)

Because `index.html` is the default filename browsers and GitHub Pages
look for, no extra config is needed to make it the homepage — just keep
that name.

## Notes

- Fonts (Noto Sans / Noto Serif) load from Google Fonts via `<link>` — no local font files needed.
- The Bloomn logo is loaded from a raw GitHub URL; if you'd rather it live in this repo too, drop the SVG into `assets/` and update the `<img src>` in `index.html` accordingly.
- Below 900px width the layout switches to a stacked, scrollable mobile view (desktop is fixed-height/non-scrolling by design).
