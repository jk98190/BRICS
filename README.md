# BRICS Policy and Development Analytics

## Overview

This project explores the evolution of BRICS through two analytical perspectives: **summit-level policy discourse** and **socioeconomic development indicators**.

Using Python, Pandas, statistical testing, data visualization, and machine learning, the project examines how BRICS summit declarations have changed over time, which policy themes receive attention, and how selected development indicators have evolved across countries.

The project combines text analytics with quantitative analysis to demonstrate how data can be used to investigate international relations, economic development, and multilateral cooperation.

## Objectives

- Analyze the evolution of BRICS summit declarations from 2009 onward.
- Identify frequently discussed policy themes and patterns of topic co-occurrence.
- Examine changes in BRICS membership, participation, and summit characteristics.
- Investigate socioeconomic development indicators, including electricity access, internet usage, renewable energy, GDP growth, healthcare expenditure, and life expectancy.
- Apply statistical tests to compare policy-theme frequencies before and after 2024.
- Explore the predictive value of selected numerical variables using machine learning.
- Identify analytical limitations and distinguish statistical associations from causal relationships.

## Datasets

The project uses two merged datasets.

### 1. BRICS Summit Declarations

**File:** `BRICS_merged.csv`

Contains 1,423 paragraph-level records and 34 columns covering summit declarations and related summit metadata.

Key variables include:

- `year` — year of the summit
- `paragraph_text` — text of the declaration paragraph
- `word_count` — number of words in a paragraph
- `topics` — policy themes associated with a paragraph
- `topic_count` — number of assigned topics
- `text_truncated` — indicates potentially truncated text
- `text_encoding_damaged` — identifies text affected by encoding problems
- `host_country` and `city` — summit location
- `member_count` and `members` — membership information
- `partner_count` and `participant_count` — participation-related information

This dataset supports text-based policy analysis, topic-frequency analysis, and comparisons across summit years.

### 2. Socioeconomic Development Indicators

**File:** `development_merged_cleaned(1).csv`

Contains 2,496 country-year-indicator records and 21 columns.

Key variables include:

- `country_name` and `country_code` — country identifiers
- `year` — observation year
- `indicator_name` and `indicator_code` — development indicator identifiers
- `value` — observed indicator value
- `unit` — measurement unit
- `is_missing` — missing-value indicator
- `value_5y_prior` — value from five years earlier, where available
- `change_5y_original_units` — five-year change in original units
- `definition` and `original_source` — indicator documentation and provenance

Selected indicators include electricity access, renewable energy consumption, internet usage, GDP growth, GDP per capita, healthcare expenditure, infant mortality, life expectancy, fertility, population, and urbanization.

**Important:** The datasets have different structures and units of analysis. They should not be joined directly without a clearly defined relationship and matching keys.

## Methodology

### 1. Data preparation

- Load the merged datasets using Pandas.
- Inspect dataset structure, variable types, and data quality.
- Identify truncated or encoding-damaged summit paragraphs.
- Exclude paragraphs flagged for encoding damage from the relevant text analyses.
- Reshape development indicators from long format into a country-year analytical table.
- Prepare numerical variables for statistical analysis and modeling.

### 2. Exploratory data analysis

Descriptive statistics are used to examine paragraph word counts, topic counts, membership, participation, and differences across summit years.

For development indicators, the analysis examines country-level observations and changes in selected indicators over time.

### 3. Policy-theme analysis

The summit declaration dataset is used to:

- Calculate the frequency of policy themes.
- Compare the distribution of themes across summit years.
- Examine which policy themes frequently appear together.
- Investigate changes in theme prevalence around the 2024 expansion period.

### 4. Statistical analysis

A chi-square test of independence is used to investigate whether the presence of selected policy themes differs between two periods:

- Before 2024
- 2024 onward

The analysis uses contingency tables and p-values to assess whether observed differences are statistically significant.

Statistical significance does not establish that BRICS expansion caused a change in policy priorities.

### 5. Development indicator analysis

The development dataset is reshaped to compare selected indicators across countries and years.

The notebook includes an analysis of life-expectancy gains, calculated as the difference between the latest and earliest available observations for each country in the analytical table.

Results must be interpreted in light of each indicator's data coverage, missing observations, and observation period.

### 6. Machine learning

The notebook explores a Random Forest regression model to predict summit paragraph length using:

- Summit year
- Topic count
- Member count
- Partner count

The model is trained on observations through 2022 and evaluated on observations after 2022.

The notebook records an R² score of approximately 0.13 for this experiment, indicating limited predictive performance on the evaluation sample. This is a useful negative result: the selected numerical features explain relatively little of the variation in paragraph length.

## Technology Stack

- **Python** — analytical programming
- **Pandas** — data cleaning, reshaping, and aggregation
- **NumPy** — numerical operations
- **Matplotlib** — data visualization
- **Scikit-learn** — machine learning and feature analysis
- **SciPy** — statistical hypothesis testing
- **Jupyter Notebook** — interactive analysis and documentation

## Repository Structure

```text
brics-policy-and-development-analysis/
├── Brics.ipynb
├── BRICS_merged.csv
├── development_merged_cleaned(1).csv
├── README.md
└── out/
    └── Generated charts and analysis outputs
```

The `out/` directory is created by the notebook for generated analytical outputs. Its contents depend on the code executed.

## Getting Started

### Prerequisites

Install Python 3 and Jupyter Notebook or JupyterLab.

### Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/brics-policy-and-development-analysis.git
cd brics-policy-and-development-analysis
```

Install the required libraries:

```bash
pip install pandas numpy matplotlib scikit-learn scipy jupyter
```

### Running the project

1. Ensure that the notebook and both CSV files are in the same directory.
2. Open the notebook:

```bash
jupyter notebook Brics.ipynb
```

3. Run the notebook cells in sequence.
4. Review the printed statistical results, tables, visualizations, and model evaluation metrics.

**Note:** The notebook references `development_merged_cleaned.csv`, whereas the supplied dataset is named `development_merged_cleaned(1).csv`. Rename the file or update the corresponding `pd.read_csv()` path before running the notebook.

## Key Analytical Findings

The notebook explores the following questions:

- Which policy themes appear most frequently in BRICS summit declarations?
- Which themes tend to appear together?
- Did the prevalence of selected themes change after 2024?
- How have selected development indicators changed across countries?
- Can basic summit characteristics predict declaration paragraph length?

The notebook includes a preliminary Random Forest regression result of approximately R² = 0.13. Other statistical findings should be reported with their exact estimates, sample sizes, and p-values after the notebook has been executed and its outputs verified.

## Limitations

- Text analyses depend on the quality and completeness of summit declaration documents.
- Topic labels reflect the dataset's existing classification and should not automatically be interpreted as objective measures of policy importance.
- The before-and-after-2024 comparison does not establish causality.
- Missing development observations can affect country comparisons and estimated changes.
- The paragraph-length model has limited predictive performance and should not be treated as a forecasting tool.
- The development dataset includes countries beyond BRICS; any BRICS-specific comparison requires an explicitly defined country selection.
- The datasets use different observational units, so cross-dataset conclusions require careful alignment and additional analysis.

## Future Improvements

- Build an interactive dashboard to explore summit themes and development indicators.
- Apply NLP techniques such as TF-IDF, document similarity, and topic modeling.
- Compare founding members, newer members, and partner countries using clearly defined groups.
- Conduct robustness checks using alternative time periods and statistical specifications.
- Improve the predictive model with stronger features and validation procedures.
- Document data sources, retrieval dates, cleaning decisions, and reproducible analytical outputs.

## Author

Developed as a data analytics project combining Python, statistical analysis, policy-text analysis, and socioeconomic development data.

## License

A license has not yet been specified. Add an appropriate open-source license before permitting reuse or redistribution.
