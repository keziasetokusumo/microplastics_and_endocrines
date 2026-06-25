# Sources & Data Provenance

Every series in this project is tagged with a **provenance class**. This is the
core of the analysis: a chart's honesty depends on the reader knowing whether a
line is a direct measurement, a statistical model fitted to data, or a
placeholder for something that was never actually measured.

| Class | Meaning |
|-------|---------|
| **MEASURED** | Direct population measurements aggregated by an authoritative body. |
| **MODELED** | A trend line / meta-regression fitted to underlying data. The line is an estimate, not a set of raw annual observations. |

---

## 1. Global plastic production — MEASURED

- **What it is:** Annual global production of polymer resins and fibers, in million tonnes (Mt).
- **Source:** Geyer, Jambeck & Law (2017), *Production, use, and fate of all plastics ever made*, Science Advances 3:e1700782, as compiled by Our World in Data; 2019 value from OECD *Global Plastics Outlook* (2022).
- **Links:** https://ourworldindata.org/grapher/global-plastics-production · https://doi.org/10.1126/sciadv.1700782 · https://doi.org/10.1787/de747aef-en
- **Period:** 1950–2019.
- **Limitations:** The CSV in `data/` uses the source's reported reference values at decadal and key years; intermediate years are connected linearly for display, not independently observed. Production is **not** the same as human microplastic *ingestion* — see note below.

## 2. Average male height by birth cohort — MEASURED

- **What it is:** Mean adult male height (cm) by year of birth, selected countries.
- **Source:** NCD Risk Factor Collaboration (NCD-RisC), *A century of trends in adult human height*, eLife 2016;5:e13410. Pooled reanalysis of 1,472 population studies, >18.6M participants.
- **Link:** https://elifesciences.org/articles/13410 · https://doi.org/10.7554/eLife.13410
- **Period:** Birth cohorts 1896–1996.
- **Limitations:** The CSV uses published endpoint reference values plus approximate intermediate cohort points for two illustrative countries (US, which plateaued; Netherlands, the tallest). It is **not** the full annual cohort series — download that from the source. Direction of travel (rising, then plateauing in some high-income countries) is robust regardless of intermediate precision.

## 2b. Male height by development tier (1896 vs 1996) — MEASURED

- **What it is:** Endpoint male height (cm) for the 1896 and 1996 birth cohorts across six countries grouped by development level, shown as a slope chart. File: `data/male_height_by_development.csv`.
- **Source:** NCD Risk Factor Collaboration, eLife 2016;5:e13410. Interactive per-country data at https://ncdrisc.org and https://ourworldindata.org/human-height.
- **Period:** Birth cohorts 1896–1996.
- **Sourced anchors (directly from the paper):**
  - Iranian men gained **16.5 cm** — the largest male increase of any country.
  - Dutch men born 1996 average **182.5 cm** — the tallest population on earth; Belgium, Estonia, Latvia, Denmark also exceed 181 cm.
  - In several sub-Saharan African countries (Niger, Rwanda, Sierra Leone, Uganda) male height **fell ~5 cm** from a peak around the early-1960s birth cohorts.
  - Shortest men today (~160 cm): Timor-Leste, Yemen, Laos. Tallest-to-shortest gap: 22–23 cm.
  - South Asia and parts of Africa saw little change over the century.
- **Limitation:** The absolute endpoint values in the CSV are **approximate reconstructions anchored to the reported gains/endpoints above**, not exact figures for every country; the paper reports gains and rankings rather than a tidy two-number table per country. The *pattern* (development gradient) is robustly sourced; treat individual absolute cm values as illustrative and pull exact per-country series from ncdrisc.org / OWID if needed.
- **Why it matters here:** Plastic/EDC exposure is highest in the tallest, most-developed countries and lowest where male height stalled or fell — the inverse of what a "plastics shrink men" mechanism predicts. The real drivers are nutrition, disease burden, and early-life conditions.

## 3. Sperm concentration trend — MODELED

- **What it is:** Meta-regression of mean sperm concentration among unselected men from North America, Europe, Australia, New Zealand.
- **Source:** Levine et al. (2017), *Temporal trends in sperm count*, Human Reproduction Update 23(6):646–659 (updated 2023, 29(2):157–176).
- **Link:** https://doi.org/10.1093/humupd/dmx022
- **Period:** 1973–2011.
- **Reported finding:** ~51.6% decline in concentration and ~59.3% decline in total sperm count over the period.
- **Limitations:** This is a **fitted model line**, not raw annual measurements. The decline is real in the data but its *cause* is contested; semen-quality secular trends are confounded by lab methods, selection, geography, and population comparability (see e.g. PMC3929517 for the skeptical view).

## 4. Total testosterone trend — MODELED

- **What it is:** Population-level, age-independent total testosterone, indexed to a baseline.
- **Source:** Travison et al. (2007), *A population-level decline in serum testosterone levels in American men*, J Clin Endocrinol Metab 92(1):196–202 (Massachusetts Male Aging Study). Consistent direction reported by Lokeshwar et al. (2020) in US adolescents/young men (NHANES).
- **Link:** https://doi.org/10.1210/jc.2006-1375
- **Period:** ~1987–2004.
- **Limitations:** Indexed (baseline = 100) to avoid asserting exact ng/dL values. This is a **specific US cohort**, not a global series, and is **modeled**. Obesity and comorbidity trends are major confounders.

## Important conceptual caveat: particles vs. additives

The hypothesis motivating this project conflates two different things:

- **Microplastic particles** — the physical fragments. Human health research on these is new and largely animal/in-vitro; there is **no authoritative decade-by-decade human ingestion series** (the widely-cited "~5 g/week" figure is a contested point estimate).
- **Plasticizer additives** — chemicals like phthalates and BPA. These are the **endocrine-disrupting chemicals (EDCs)** that the androgen-health literature actually studies (anti-androgenic effects on sperm, testosterone, anogenital distance).

The androgen-related concern is mostly about the **additives**, not the particles. And there is no single measurable quantity for how "male" a genome is expressed; androgen levels, sperm parameters, and androgen-dependent development are.

## On causation

Two time series moving together (or apart) cannot establish causation. Note in
particular that **male height — an androgen- and growth-influenced trait — rose**
across the same century plastics exploded, cutting against a simple
"plastics suppress male development" reading. Treat the overlay as hypothesis-generating, not
confirmatory.
