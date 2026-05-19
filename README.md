# hush-site

The website for **Hush**, a local-LLM chat app for Apple Vision Pro.

Deployed via GitHub Pages at https://juergen-kc.github.io/hush-site/.

## Pages

- `/` — Landing page (one-paragraph hook + screenshot + what-you-get / what-you-don't-get).
- `/privacy/` — Privacy policy. URL configured in App Store Connect for the Hush app record.

## Structure

```
.
├── index.html              Landing page
├── privacy/index.html      Privacy policy
├── assets/
│   ├── styles.css          Shared CSS — PAPER/TERM tokens via prefers-color-scheme
│   ├── favicon.svg         "h" + cursor mark, adapts to dark mode
│   └── screenshot.jpg      Hero screenshot (1280×720 JPEG)
├── .nojekyll               Skip Jekyll processing — serve files as-is
└── README.md               This file
```

The site is plain HTML + CSS — no build step, no JS, no framework. Edit
files directly and push to `main`. GitHub Pages serves them as-is.

## Theme tokens

The CSS palette mirrors the app's theme tokens exactly so the site
visually matches what users see in the headset. Source of truth lives in:
- `Hush/Theme/PaperTheme.swift` — light mode
- `Hush/Theme/TermTheme.swift` — dark mode

If those change in the app, update `assets/styles.css` to match.

## Local preview

```sh
python3 -m http.server 8000
open http://localhost:8000/
```

Note: links use absolute paths under `/hush-site/` to match the GitHub
Pages deploy URL. For pure-local preview at `localhost:8000/`, the links
will 404 — that's expected. To preview at root, run:

```sh
python3 -m http.server 8000 --directory .
# then open http://localhost:8000/hush-site/  (symlink trick) or test on Pages
```

The simplest sanity check is to push and view the live URL.

## License

Site content © 2026 Klaassen Consulting. The privacy policy text may be
referenced under fair use for understanding Hush's data practices.
