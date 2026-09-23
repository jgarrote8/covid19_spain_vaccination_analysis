# COVID-19 Pandemic in Spain and the Influence of Vaccination

Analysis of the COVID-19 pandemic in Spain and its relationship with the evolution of vaccination, developed as a practical case study for the course **Mathematics for Data Analysis with R**.

The project analyzes epidemiological, vaccination and mortality data for **Spain, Extremadura and the Canary Islands**, using R and R Markdown to process the data and generate static and interactive visualizations.

> **Original analysis:** December 9, 2021

---

## Overview

This project explores the evolution of the COVID-19 pandemic in Spain before and after the beginning of the vaccination campaign.

The analysis focuses on the relationship between vaccination coverage and several epidemiological indicators, including:

* Daily COVID-19 cases
* Hospitalizations
* ICU admissions
* Deaths
* Cumulative cases and deaths
* 7-, 10- and 14-day incidence rates
* Vaccination progress
* Vaccines delivered by manufacturer
* COVID-19 cases by age group
* General mortality

The analysis is performed at both the national level and for two autonomous communities:

* 🇪🇸 Spain
* Extremadura
* Canary Islands

The same analytical workflow is reused for the three territories, adapting the data filtering to each autonomous community.

---

## Objectives

The main objective of the project is to examine the influence of vaccination on the evolution of the COVID-19 pandemic by comparing epidemiological data from before and after the beginning of the vaccination campaign.

More specifically, the project aims to:

* Analyze the daily evolution of the pandemic.
* Study cases, hospitalizations, ICU admissions and deaths.
* Calculate epidemiological indicators such as cumulative incidence.
* Analyze the evolution of vaccination in Spain.
* Compare vaccination progress with COVID-19 case evolution.
* Explore differences between age groups.
* Compare mortality during 2020 and 2021.
* Examine differences between Spain and selected autonomous communities.

---

## Data Sources

The analysis uses publicly available data from several sources.

### Spanish Ministry of Health

COVID-19 epidemiological data were obtained from the Spanish Ministry of Health / ISCIII, including datasets containing information on diagnosed cases, hospitalizations, ICU admissions and deaths.

The R Markdown document imports these datasets directly from their online URLs.

### Datadista

Vaccination data were obtained from the **Datadista COVID-19 datasets repository on GitHub**.

The dataset is downloaded directly from GitHub during execution of the R code.

The vaccination data include information such as:

* Vaccination dates
* Administered doses
* Delivered doses
* Vaccine manufacturer

The project specifically analyzes vaccines from Pfizer, Moderna, AstraZeneca and Janssen.

### MoMo / ISCIII

General mortality data were obtained from the **MoMo (Monitoring of Excess Mortality) system** and used to compare mortality patterns between 2020 and 2021.

---

## Methodology

The analysis follows a data-processing and visualization workflow implemented entirely in R.

### 1. Data acquisition

The epidemiological, vaccination and mortality datasets are imported directly from their respective online sources.

This means that the datasets themselves are not stored in the repository; the R Markdown code retrieves them when executed.

### 2. Data cleaning and transformation

The imported datasets are processed using R to:

* Filter observations by territory.
* Aggregate observations by date.
* Convert variables to appropriate data types.
* Handle missing values.
* Calculate daily vaccination doses.
* Combine data from different provinces when necessary.
* Prepare datasets for visualization.

For example, the Canary Islands analysis combines data from the provinces of **Las Palmas and Santa Cruz de Tenerife** before aggregating the epidemiological variables by date.

### 3. Epidemiological indicators

The project calculates several indicators to describe the evolution of the pandemic, including:

* Daily cases
* Daily deaths
* Daily hospitalizations
* Daily ICU admissions
* Cumulative totals
* Cases per 100,000 inhabitants
* Deaths per 100,000 inhabitants
* Hospitalizations per 100,000 inhabitants
* ICU admissions per 100,000 inhabitants
* 7-day cumulative incidence
* 10-day cumulative incidence
* 14-day cumulative incidence

### 4. Vaccination analysis

Vaccination data are cleaned and transformed before analyzing:

* Daily administered doses
* Cumulative vaccination
* Doses delivered by manufacturer
* Percentage of vaccinated population

The project also creates a time-series representation of vaccine deliveries and uses `ggfortify` to visualize vaccine deliveries by manufacturer.

### 5. Vaccination vs. pandemic evolution

The project compares vaccination progress with the evolution of COVID-19 cases.

Because the dates in the epidemiological and vaccination datasets do not always correspond exactly, `fuzzyjoin` is used to match observations by date.

Interactive visualizations are then generated using `plotly`.

### 6. Age-group analysis

COVID-19 cases are also compared between different age groups at different points during the vaccination campaign.

`ggpubr` is used to combine and format multiple plots into comparative figures.

### 7. Mortality analysis

General mortality data are analyzed using MoMo data.

The project compares observed deaths during 2020 and 2021 and also examines mortality by age group. `lattice` is used for some of the multivariable visualizations.

---

## R Markdown and knitr

The project was developed using **R Markdown**.

The original `.Rmd` document combines:

* Markdown text
* R code
* Generated figures
* Interactive visualizations

`knitr` is used to process the R Markdown document and generate the final HTML report.

The document also configures `knitr` to display the R code alongside its results while suppressing warnings and messages in the generated report.

Interactive graphics require `htmlwidgets` so that the required JavaScript components can be included correctly in the generated HTML document.

---

## R Packages

The project uses several R packages for data manipulation, visualization and interactive graphics.

### Data manipulation

* `tidyverse`
* `dplyr`
* `tidyr`
* `readr`
* `stringr`
* `forcats`
* `purrr`

`tidyverse` provides the main tools used to import, transform and manipulate the datasets.

### Visualization

* `ggplot2`
* `ggpubr`
* `lattice`
* `ggfortify`

### Interactive visualization

* `plotly`
* `dygraphs`
* `htmlwidgets`

### Time-series and date handling

* `xts`
* `lubridate`

### Data joining

* `fuzzyjoin`

---

## Visualizations

The project generates a wide range of visualizations, including:

* Daily COVID-19 cases
* Daily deaths
* Hospitalizations
* ICU admissions
* Cumulative cases and deaths
* Incidence over 7, 10 and 14 days
* Cases per 100,000 inhabitants
* Vaccination progress
* Vaccine deliveries by manufacturer
* Vaccination vs. COVID-19 cases
* COVID-19 cases by age group
* General mortality
* Mortality by age group
* 2020 vs. 2021 mortality comparisons

Some visualizations are interactive, allowing the user to explore different periods of the pandemic directly in the HTML report. For example, `dygraphs` is used to create an interactive vaccination time series with a selectable date range.

---

## Main Findings

The original analysis identified several patterns across Spain, Extremadura and the Canary Islands.

### Pandemic evolution

The daily epidemiological indicators showed similar broad trends across the territories, with particularly high levels of cases, hospitalizations and deaths during the first months of 2021, followed by a progressive reduction in several indicators.

### Regional differences

The 14-day cumulative incidence presented different patterns between Spain and the two autonomous communities.

The original analysis identified:

* **10 peaks** in Spain
* **7 peaks** in Extremadura
* **9 peaks** in the Canary Islands

The Canary Islands also presented a particularly high incidence peak during the summer of 2021. The original report discusses summer tourism as a possible factor.

### Vaccination

The analysis found that Pfizer and Moderna represented the most consistently delivered vaccines in the analyzed data.

The comparison between vaccination and COVID-19 cases showed changes in their relative evolution during 2021, including a period during May when the vaccination curve exceeded the cases-per-100,000 curve, followed by a summer reversal and another change in July.

### Mortality

The mortality analysis compared observed deaths during 2020 and 2021 and identified a marked increase in deaths during April 2020 compared with April 2021 in Spain and Extremadura.

### Age groups

The analysis observed a reduction in COVID-19 cases across most age groups during the vaccination period, while the 0–9 age group showed comparatively similar values in the analyzed comparison. The original report discusses vaccination coverage as a possible explanation and proposes reassessing the data once sufficient vaccination coverage had been reached in that group.

---

## Interpretation

The project explores the **relationship between vaccination and the evolution of the pandemic** through temporal comparisons and graphical analysis.

The original report describes an association between increasing vaccination and improvements in several pandemic indicators. However, the analysis also discusses other factors that may affect the evolution of the pandemic, including public-health measures and tourism.

Therefore, the results should be interpreted as an **observational analysis of temporal trends and associations**, rather than as a controlled causal analysis of the effect of vaccination.

---

## Repository Structure

```text
.
├── memoria.Rmd
├── memoria.html
└── README.md
```

### `memoria.Rmd`

The complete R Markdown source containing:

* Explanatory text
* R code
* Data acquisition
* Data processing
* Statistical calculations
* Visualizations
* Analysis and conclusions

### `memoria.html`

The HTML report generated from the R Markdown document using `knitr`.

It contains the complete rendered analysis, including the explanations, code output, static figures and interactive visualizations.

### `README.md`

This document provides an overview of the project, methodology, data sources and main findings.

---

## Reproducibility

The datasets are **not included directly in the repository**.

Instead, the R Markdown source downloads the required datasets from their original online sources when the analysis is executed.

To reproduce the analysis:

1. Install R and RStudio.
2. Install the required R packages.
3. Open `memoria.Rmd`.
4. Run the R Markdown document using **Knit → Knit to HTML**.
5. `knitr` will execute the R code and generate the corresponding HTML report.

> **Important:** The original analysis was completed on December 9, 2021. Because some datasets are retrieved directly from external URLs, running the code today may produce different results if those external datasets have subsequently changed.

---

## References

The original project references the following sources:

* Spanish Ministry of Health / ISCIII COVID-19 datasets
* Datadista COVID-19 datasets
* MoMo mortality data
* R and `knitr` documentation
* `tidyverse` documentation
* `lubridate` documentation
* `lattice` documentation
* `plotly` documentation
* `dygraphs` and `htmlwidgets` documentation
* `fuzzyjoin` documentation
* `ggfortify` documentation
* `ggpubr` documentation

The complete list of references used in the original report is available at the end of `memoria.Rmd`.

---

## Academic Context

**Course:** Mathematics for Data Analysis with R
**Type:** Practical case study
**Original date:** December 9, 2021
**Author:** Javier Garrote

---

## Author

**Javier Garrote**

Bioinformatics & Biochemistry

---

## License

No specific software license was defined in the original project.
