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
- **Source:** Geyer, Jambeck & Law (2017), *Production, use, and fate of all plastics ever made*, Science Advances 3:e1700782; 2019 value from OECD *Global Plastics Outlook* (2022).
- **Links:** https://doi.org/10.1126/sciadv.1700782 · https://doi.org/10.1787/de747aef-en
- **Period:** 1950–2019.
- **Limitations:** The CSV in `data/` uses the source's reported reference values at decadal and key years; intermediate years are connected linearly for display, not independently observed. Production is **not** the same as human microplastic *ingestion* — see note below.

## 2. Average male height by birth cohort — MEASURED

- **What it is:** Mean adult male height (cm) by year of birth, selected countries.
- **Source:** NCD Risk Factor Collaboration (NCD-RisC), *A century of trends in adult human height*, eLife 2016;5:e13410. Pooled reanalysis of 1,472 population studies, >18.6M participants.
- **Link:** https://elifesciences.org/articles/13410 · https://doi.org/10.7554/eLife.13410
- **Period:** Birth cohorts 1896–1996.
- **Limitations:** The CSV uses published endpoint reference values plus approximate intermediate cohort points for two illustrative countries (US, which plateaued; Netherlands, the tallest). It is **not** the full annual cohort series — download that from the source. Direction of travel (rising, then plateauing in some high-income countries) is robust regardless of intermediate precision.

## 2b. Male height by development level (1985 vs 2019, 19-year-olds) — MEASURED

- **What it is:** Mean height (cm) of 19-year-old boys in 1985 and 2019 across four countries/groups spanning development levels, shown as a slope chart. File: `data/male_height_19yo_1985_2019.csv`. This replaces an earlier 1896→1996 birth-cohort version so the developed-vs-developing comparison is recent.
- **Source:** NCD Risk Factor Collaboration, *Height and body-mass index trajectories of school-aged children and adolescents from 1985 to 2019*, **Lancet** 2020;396:1511–1524 (2,181 studies, 65M participants). Per-country and regional CSVs: https://www.ncdrisc.org/data-downloads-height.html
- **Link:** https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(20)31859-6/fulltext
- **Period:** Survey years 1985–2019 (19-year-olds).
- **Sourced / exact anchors:**
  - **United Kingdom: 176.4 cm (1985) → 178.2 cm (2019)** — exact, taken directly from the NCD-RisC country CSV. UK fell in the global ranking from 28th to 39th tallest.
  - **China: +8.0 cm** over the period (sourced), with global rank rising from **150th to 65th** — among the largest gains, a catch-up pattern shared with South Korea and parts of Southeast Asia.
  - **Netherlands: 183.8 cm (2019)** — sourced; the tallest 19-year-old boys on earth (Montenegro, Estonia, Bosnia & Herzegovina next).
  - **Shortest in 2019 (~160 cm):** Timor-Leste, Laos, Solomon Islands, Papua New Guinea; the tallest-to-shortest national gap exceeds **20 cm**. Many sub-Saharan African countries stagnated or declined.
  - Cross-check (exact, from the NCD-RisC regional CSV): Central & Eastern Europe boys 176.2 (1985) → 178.3 (2019), consistent with the UK plateau.
- **Limitation:** UK endpoints are exact. China's 1985 value is derived (2019 minus the sourced +8 cm); Netherlands' 1985 value and the low-income line's endpoints are approximate, anchored to the sourced 2019 figures. The country-level download files are gated to URLs that have appeared in search/fetch results, so not every country could be pulled directly; the *pattern* (developed plateau, developing catch-up, low-income stagnation) is robustly sourced. Pull any exact per-country series from ncdrisc.org if needed.
- **Relevance:** Differences in male height across countries track development indicators — nutrition, disease burden, and early-life conditions. Height is not a specific measure of androgen activity, so it is an indirect indicator for questions about endocrine exposure.

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

Most endocrine research relevant to this topic concerns the **additives**, not the particles. There is no single measurable quantity for how "male" a genome is expressed; the measurable outcomes are androgen levels, sperm parameters, and androgen-dependent development.

## On causation

Two time series moving together (or apart) cannot, on their own, establish
causation. Mean male height rose over the twentieth century and has plateaued in
high-income countries; because height is influenced predominantly by nutrition
and disease, it is an indirect indicator for questions about endocrine exposure.
The overlay in the project is descriptive and does not demonstrate a causal
relationship.
