# Police Crime Power BI Dashboard

A decision-support dashboard built in **Microsoft Power BI** to help police leadership monitor recorded crime, compare forces fairly and investigate unusual or seasonal movement.

The project uses **three years of monthly recorded crime data** across:

- West Midlands Police
- Staffordshire Police
- West Mercia Police
- Warwickshire Police

The dashboard is designed for senior, non-technical users who need to move quickly from a headline change to a focused operational question.

## Business purpose

The report is built around three leadership tasks:

**Monitor → Compare → Investigate**

- **Monitor** overall recorded crime and category movement over time
- **Compare** police forces using both total volume and population-adjusted rates
- **Investigate** seasonal patterns, unusual increases and categories requiring deeper review

## Power BI report structure

The PBIX contains **2 report pages**:

### 1. Crime Overview

The overview page includes:

- headline KPI cards
- monthly recorded-crime trend
- average monthly crime rate per 1,000 residents by force
- top 5 crime categories by recorded volume
- recorded crime and officer strength by reporting year
- slicers for police force, crime category and date

### 2. Crime Investigation & Seasonality

The investigation page includes:

- seasonal crime patterns by reporting year
- crime rate vs employment deprivation by police force
- monthly trends for the top 5 crime categories
- average officers per 100,000 KPI
- average monthly crime rate per 1,000 KPI
- force and crime-category slicers

The underlying report model contains two visible tables:

```text
Police Crime Data - OUTPUT
DateTable
```

## Key Power BI measures

Measures referenced by the report include:

- `Latest Month YoY Change %`
- `Average Monthly Crime Rate per 1,000`
- `Average Officers per 100,000`

An exact DAX expression retained in the PBIX query view is:

```DAX
Average Monthly Crime Rate per 1,000 =
DIVIDE(
    SUM('Police Crime Data - OUTPUT'[Crime rate per 1,000]),
    DISTINCTCOUNT('Police Crime Data - OUTPUT'[Month])
)
```

See [DAX measure reference](dax/average-monthly-crime-rate.dax).

## Key findings

### 1. West Midlands carries the highest burden

West Midlands has the highest total recorded crime volume in the dataset at approximately **933k** records.

It also remains highest after adjusting for population, with an average monthly crime rate of approximately **8.5 per 1,000 residents**.

This matters because total volume reflects workload, while the population-adjusted rate provides a fairer comparison between forces of different sizes.

### 2. A small number of categories drive overall recorded crime

**Violence and sexual offences account for approximately 44% of total recorded crime**, with around **699k** recorded offences in the analysis.

Other high-volume categories include:

- Shoplifting: ~151k
- Criminal damage and arson: ~134k
- Vehicle crime: ~127k
- Public order: ~114k
- Other theft: ~111k

This means movement in a high-volume category can materially change the overall headline.

### 3. Seasonal movement is visible

Across the three-year period, recorded crime is generally higher around late spring and summer.

**July has the highest average monthly volume**, while October also appears as a recurring elevated month.

The dashboard uses this as an operational planning signal rather than claiming a permanent long-term seasonal effect.

### 4. Recent increases are category-specific

In **2025/26 vs 2024/25**:

| Category | YoY change |
|---|---:|
| Drugs | **+15.3%** |
| Possession of weapons | **+8.5%** |
| Robbery | **+8.0%** |
| Violence and sexual offences | **+3.8%** |
| Shoplifting | **-5.0%** |
| Burglary | **-5.0%** |
| Vehicle crime | **-7.1%** |

The dashboard therefore supports targeted investigation rather than treating movement as an across-the-board increase.

## Leadership actions

The analysis highlights four areas for further review:

1. **Staffordshire trend** — latest-year total increased by 4.6% vs 2024/25; investigate the categories and months driving this.
2. **Drugs, robbery and weapons** — these categories increased year on year and should be prioritised for deeper review.
3. **West Midlands rate pressure** — compare the high population-adjusted crime rate alongside category mix and wider context.
4. **Seasonal readiness** — use historic monthly patterns to distinguish expected seasonal movement from unusual increases.

## Repository structure

```text
.
├── README.md
├── powerbi/
│   └── README.md
├── dax/
│   └── average-monthly-crime-rate.dax
├── documentation/
│   ├── executive-summary.md
│   ├── report-structure.md
│   ├── insights-and-actions.md
│   └── assumptions-and-limitations.md
└── .gitignore
```

## Power BI project file

The original `.pbix` was inspected directly to document the report structure, visuals, model tables and DAX accurately. The current GitHub connection supports repository text/code changes but does not expose a binary-file upload action, so the `.pbix` itself is not committed here.

The portfolio documentation is based on the submitted Power BI file rather than being reconstructed from the presentation alone.

## Assumptions and limitations

The dashboard is intended to support **prioritisation and follow-up**, not prove causation.

Important limitations include:

- recorded crime does not represent all crime occurring in an area
- recording and enforcement practices can affect recorded volumes
- force-level averages can hide local neighbourhood variation
- three years of monthly data is useful for operational seasonality but not enough to establish a permanent long-term pattern
- population is held constant using the selected 2024 estimate so rates remain comparable across the period
- the reporting scope excludes outcomes and stop-and-search activity

See [Assumptions & Limitations](documentation/assumptions-and-limitations.md).

## What this project demonstrates

This project demonstrates my ability to use **Power BI, DAX, data modelling, KPI design, interactive filtering and visual analytics** to turn a processed dataset into a concise decision-support tool for senior stakeholders.

The focus is not simply on displaying data, but on helping users answer:

**What changed? Where did it change? Why might it matter? What should be reviewed next?**

---

**Tarandeep Rehlon**  
Data Analyst / Trainee Data Consultant portfolio project
