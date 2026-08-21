# ECON-5371 Interactive Widgets

Companion interactive widgets for *ECON-5371: Time Series Analysis and Forecasting*.
Static HTML/JS, no build step, no server — deploys directly via GitHub Pages.

Live site (once deployed): `https://ncachanosky.github.io/ECON-5371-widgets/`

## Structure

```
.
├── index.html              # Landing page, links to all widgets
└── widgets/
    └── arma/
        └── index.html       # ARMA(2,2) explorer (Chapter 3)
```

Each future widget gets its own folder under `widgets/`, e.g. `widgets/garch/index.html`,
`widgets/breaks/index.html`, matching the pattern already used for `arma/`.
This keeps each widget's URL clean (`.../widgets/garch/`) and self-contained —
every widget is a single standalone HTML file with no shared dependencies beyond
CDN-hosted Plotly.js, so folders can be added or edited independently without
touching anything else on the site.

## Deploying for the first time

From this folder:

```bash
git init
git add .
git commit -m "Initial widget site: ARMA(2,2) explorer + landing page"
git branch -M main
git remote add origin https://github.com/ncachanosky/ECON-5371-widgets.git
git push -u origin main
```

Then on GitHub:

1. Go to the repo → **Settings → Pages**
2. Under "Build and deployment," set **Source: Deploy from a branch**
3. Set **Branch: `main`**, folder: **`/ (root)`**
4. Save. GitHub will publish to `https://ncachanosky.github.io/ECON-5371-widgets/`
   within a minute or two.

## Adding a new widget later

```bash
mkdir -p widgets/<name>
# save the new widget's HTML as widgets/<name>/index.html
# add a card for it on index.html, linking to widgets/<name>/
git add .
git commit -m "Add <name> widget"
git push
```

No render step, no `quarto render`, no `docs/` folder — this repo is intentionally
separate from the `ECON-5371` textbook/slides repo so that book renders never
touch widget files and vice versa.

## Linking from the textbook

From any chapter `.qmd` in the main `ECON-5371` repo, link out with a plain
Markdown link or a styled callout, e.g.:

```markdown
::: {.callout-note icon=false}
## Explore this interactively
Try the [ARMA(2,2) Explorer](https://ncachanosky.github.io/ECON-5371-widgets/widgets/arma/)
to see how the AR and MA coefficients shape the series, ACF, and PACF.
:::
```
