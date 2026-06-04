# Clinical Trial Analyzer (v1.0)

**Clinical Trial Analyzer** supports clinical trial strategy development for life cycle management planning of your asset(s). It provides (multi)indication-driven statistical analysis of announced clinical trials on [ClinicalTrials.gov](https://clinicaltrials.gov).


---

## Quick Start

**1. Export your data from ClinicalTrials.gov**

Go to [clinicaltrials.gov](https://clinicaltrials.gov) → Search → filter to **Interventional trials only** → Download → **CSV / All Studies**

**2. Open the tool**

Open `CT_analyzer_v01.1.html` in any modern browser (Chrome, Edge, Firefox, Safari).

**3. Drop your CSV**

Drag and drop the downloaded CSV onto the landing screen. The dashboard renders immediately — all processing runs locally in your browser.

---


## Features

### Trial Overview
Status × phase breakdown table and top 15 sponsors by phase. Supports phase merging (Phase 1/2 → Phase 2, Phase 2/3 → Phase 3).

### Trial Length / Enrollment
- **Duration chart** — stacked bar showing average primary duration and total trial length per phase, with values annotated on bars
- **Enrollment chart** — grouped bars comparing average vs. median enrollment per phase
- Download charts as PNG or raw data as Excel

### Enrollment Pressure
Estimates patients recruited per calendar year by spreading each trial's enrollment across its duration (primary completion date). Stacked by phase. Downloadable as PNG and Excel.

### Patient Criteria & Endpoints
- Top 20 primary and secondary endpoint labels, frequency-ranked and sortable by phase
- Timepoint distribution (normalised: 6 months = 24 weeks, 1 year = 48 weeks)
- Demographics: sex and age category distribution by phase
- Adverse event clustering: all AE/TEAE/treatment-emergent variants grouped under a single label

### Trial Table
Sortable, searchable, paginated trial list. Outlier trials (enrollment > mean + 2 SD per phase) are highlighted and reviewable via the outlier modal.

### Filters
- Indication groups (10 metabolic/liver disease categories, selectable individually)
- Funder type: IST (industry-sponsored) vs. IIT (investigator-initiated)
- Status exclusions: suspended/withdrawn/unknown, terminated, unclear phase
- Start year range

---

## Input Format

Standard ClinicalTrials.gov CSV export. The tool uses these columns:

`NCT Number` · `Study Title` · `Study URL` · `Study Status` · `Phases` · `Funder Type` · `Enrollment` · `Start Date` · `Primary Completion Date` · `Completion Date` · `Conditions` · `Sponsor` · `Sex` · `Age` · `Primary Outcome Measures` · `Secondary Outcome Measures` · `Interventions` · `Brief Summary` · `Locations`

---

## Optional: Python Pre-processor (AI Criteria Extraction)

For AI-generated patient criteria summaries (typical patient profile, inclusion/exclusion patterns), run the Python pre-processor with an Anthropic API key:

```bash
pip install anthropic
export ANTHROPIC_API_KEY=sk-ant-...
python process_trials.py your_data.csv --ai-extract
```

This generates `data_bundle.js`. Place it alongside the HTML file — it loads automatically and enables the **AI Criteria** tab.

---

## File Structure

```
├── CT_analyzer_v01.1.html   ← the tool (open this)
├── BII_bg.jpg.jpg           ← landing page background image
├── process_trials.py        ← optional: Python pre-processor for AI extraction
├── requirements.txt         ← optional: Python dependencies
└── README.md
```

All other dependencies (Chart.js, SheetJS, PapaParse, Inter font) load from CDN — no installation required.

---

## Feedback & Support

Use the **💬 Feedback / Support** button in the bottom-right corner of the tool
