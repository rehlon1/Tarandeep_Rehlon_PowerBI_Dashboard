# Report Structure and Technical Notes

This documentation is based on the structure stored in the Power BI PBIX file.

## Data model

Two visible model tables are present:

```text
Police Crime Data - OUTPUT
DateTable
```

The `DateTable` is used by report visuals for fields such as:

- Date
- Month Name
- Reporting Year

The main crime table supplies:

- Crime count
- Crime type
- Police force
- Crime rate per 1,000
- Employment deprivation rate (%)
- officer-strength context
- report measures

## Report page 1 - Crime Overview

**11 visuals**

### KPI cards

The page includes multiple card visuals, including:

- total crime count
- latest-month crime reporting
- latest-month year-on-year change

### Charts

**Monthly Crime Trend**  
Uses date, crime count and police force.

**Average Monthly Crime Rate per 1,000 Residents**  
Compares the population-adjusted crime rate between forces.

**Top 5 Crime Types by Recorded Volume**  
Uses a Top N query to surface the highest-volume categories.

**Recorded Crime and Officer Strength by Reporting Year**  
Combines crime volume with officer-strength context across reporting years.

### Slicers

- Police force
- Crime type
- Date

## Report page 2 - Crime Investigation & Seasonality

**7 visuals**

### Charts

**Seasonal Crime Patterns by Reporting Year**  
Compares monthly crime movement between reporting years.

**Crime Rate and Employment Deprivation by Police Force**  
Uses a scatter plot to provide socioeconomic context alongside population-adjusted crime rates.

**Monthly Trends for Top 5 Crime Types**  
Allows category trends to be compared across time.

### KPI cards

- Average Officers per 100,000
- Average Monthly Crime Rate per 1,000

### Slicers

- Police force
- Crime type

## Measures referenced by report visuals

The PBIX report definition references:

- `Latest Month YoY Change %`
- `Average Monthly Crime Rate per 1,000`
- `Average Officers per 100,000`

The Power BI DAX query view also contains the full expression for `Average Monthly Crime Rate per 1,000`, which is included in the repository under `dax/`.
