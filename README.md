# Plastics & male hormonal health: what the data can and can't say

A data visualization exploring how microplastics have increased over time, and whether microplastics suppress male-typical traits.

The short answer the data supports: **plastic exposure has risen dramatically;
some androgen-sensitive markers (sperm count, testosterone) show declines in
certain populations that are real but contested and heavily confounded; male
height — an androgen-influenced trait — actually *rose* over the same period;
and the relevant endocrine science is mostly about plasticizer *additives*
(phthalates, BPA), not microplastic particles. Correlated time series cannot
establish causation.**

This repo renders that argument as a static website (`index.html`) with every
data series tagged **measured**, **modeled**, or **unmeasurable**.

## What's here

```
.
├── index.html        # the site — open locally or serve via GitHub Pages
├── SOURCES.md        # full provenance: source, link, period, limitations per series
├── data/             # the underlying CSVs, each row tagged with provenance
│   ├── plastic_production.csv
│   ├── male_height_ncdrisc.csv
│   ├── male_height_by_development.csv
│   ├── sperm_count_levine.csv
│   └── testosterone_trend.csv
├── LICENSE
└── README.md
```

## View it

**Locally:** open `index.html` in any browser (it's self-contained; charts load
Chart.js from a CDN at runtime).

**On the web via GitHub Pages:**
1. Push this repo to GitHub.
2. Repo → **Settings** → **Pages**.
3. Under *Build and deployment*, set **Source: Deploy from a branch**, branch
   `main`, folder `/ (root)`, and save.
4. Your site goes live at `https://<your-username>.github.io/<repo-name>/`.

(If you prefer, move `index.html` into a `docs/` folder and select `/docs` as the
Pages folder — handy if you later add a build step.)

## Data integrity

The point of this project is *not* to win an argument with a chart. Read
[`SOURCES.md`](SOURCES.md) before reusing anything: it spells out which lines are
real measurements, which are fitted model estimates, and which are placeholders
for things that were never measured. Datasets retain their original licenses
(Our World in Data is CC-BY; cite the underlying papers).

## License

Code in this repo: MIT (see `LICENSE`). Data: see per-source licensing in
`SOURCES.md`.
