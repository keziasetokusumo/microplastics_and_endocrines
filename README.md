# Plastics & male hormonal health: what the data can and can't say

A data visualization exploring how microplastics have increased over time, and whether microplastics suppress male-typical traits.

The short answer the data supports: **plastic exposure has risen dramatically;
some androgen-sensitive markers (sperm count, testosterone) show declines in
certain populations that are real but contested and heavily confounded; male
height — an androgen-influenced trait — actually *rose* over the same period;
and the relevant endocrine science is mostly about plasticizer *additives*
(phthalates, BPA), not microplastic particles. Correlated time series cannot
establish causation.**

This repo renders that argument as a static website.

## What's here

```
.
├── data/             # the underlying CSVs
│   ├── plastic_production.csv
│   ├── male_height_ncdrisc.csv
│   ├── male_height_19yo_1985_2019.csv
│   ├── sperm_count_levine.csv
│   └── testosterone_trend.csv
├── LICENSE
├── README.md
├── SOURCES.md        # source, link, period, limitations per series
└── index.html        # the data visualization

```

## View it



## Data integrity

The point of this project is *not* to win an argument with a chart. Read
[`SOURCES.md`](SOURCES.md) before reusing anything: it spells out which lines are
real measurements, which are fitted model estimates, and which are placeholders
for things that were never measured. Datasets retain their original licenses;
cite the primary papers (NCD-RisC, Geyer et al., Levine et al., Travison et al.) and OECD.

## License

Code in this repo: MIT (see [`LICENSE`](LICENSE)). Data: see per-source licensing in
[`SOURCES.md`](SOURCES.md).
