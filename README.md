# COVID-19 Global Trend and Risk Analysis

Case study project analyzing global COVID-19 case, death, recovery, and testing data,
identifying the countries and trends that mattered most, and building a set of interactive
Plotly visualizations and risk-ratio metrics. Built as part of my analytics portfolio at
gimeno.tech (https://www.gimeno.tech).

## Business problem

During a fast-moving global health event, raw case counts alone don't tell you much. This
project turns a country-by-country COVID-19 snapshot into a set of comparable metrics: case
fatality rate, tests-to-confirmed ratio, deaths-to-recovered ratio, and more, to answer which
countries were hit hardest, which were testing enough to see the full picture, and which had
the worst (or best) outcomes once someone was infected.

## Approach

The notebook loads country-level COVID-19 snapshot data (cases, deaths, recovered, active,
population, and testing figures per country), then explores it with treemaps of total
cases/deaths/recovered/active by country, line plots of the global trend over time, and bar
charts ranking the 20 most-affected countries by multiple metrics (cases, tests-to-population
ratio, recovered, active). It then ranks the top 10 countries by total cases, deaths,
recovered, and active cases using donut charts.

From there it derives four risk ratios. Case Fatality Rate (deaths divided by confirmed cases)
shows how severe an outcome is once infected. Deaths-to-Recovered ratio reflects recovery
strength, where lower is better. Tests-to-Confirmed ratio is a rough proxy for how much a
country's testing coverage could be under- or over-stating its true case count. Serious-to-
Deaths ratio rounds out the risk picture.

Finally, the notebook lets you drill down into any single country's full case, active,
recovered, and death time series, and exports each chart as a standalone interactive HTML
file for the portfolio site.

## Repo structure

Covid19_Data/data/incoming/ holds the raw source CSV, and Covid19_Data/notebooks/ holds the
end-to-end analysis notebook. The interactive charts this notebook produces are published
live on the portfolio site rather than duplicated in this repo; running the notebook
regenerates them locally as standalone HTML files in a git-ignored charts/ folder.

Note: this repo previously held a handful of individually-uploaded chart HTML exports at the
repo root, from an earlier, less structured pass. Those are being consolidated under the
charts/-is-git-ignored convention used across the rest of this portfolio.

## Running it

Install dependencies with "pip install -r requirements.txt", then open
notebooks/Portfolio_Covid_19_Global_Trend_and_Risk_Analysis.ipynb in Jupyter. Running all
cells top to bottom reproduces every chart (charts/, git-ignored) from the raw data in
data/incoming/. Paths are resolved relative to the project root, so it runs the same whether
you launch it from the repo root or from inside notebooks/.

## Key findings

A small number of countries account for a disproportionate share of global confirmed cases,
deaths, recovered, and active cases; the top-20 and top-10 breakdowns make the concentration
clear. Case Fatality Rate varies substantially by country, reflecting differences in
healthcare capacity, population age structure, and how thoroughly each country was testing (a
country that only tests severe cases will show an inflated CFR relative to one testing
broadly). The tests-to-confirmed ratio highlights that raw case counts aren't directly
comparable across countries without accounting for how much testing was actually done.
Deaths-to-recovered ratio and serious-to-deaths ratio give a more outcome-focused view than
raw totals, surfacing countries where a confirmed case was more likely to end badly.

## Data source

The dataset used here, worldometer_data.csv, is a country-level COVID-19 snapshot in the
style of the well-known "COVID-19 Dataset" on Kaggle
(https://www.kaggle.com/datasets/imdevskp/corona-virus-report): cases, deaths, recovered,
active, population, and testing figures per country.

## Notes

This is a from-scratch analytics/portfolio project; it is not a general-purpose epidemiology
library. Column names and figures are specific to this dataset's snapshot in time and are not
kept up to date with current case counts.
