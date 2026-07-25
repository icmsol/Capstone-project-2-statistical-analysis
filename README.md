# Capstone Project 2: Statistical Analysis of California Public Procurement

## Project Overview

This project conducts a reproducible statistical analysis of California public-sector procurement opportunities to identify patterns relevant to ICM Solutions workforce and business-development planning. It combines five complete fiscal years of completed solicitations from California Cal eProcure with records from the County of El Dorado and the City of Sacramento. Current open opportunities are maintained as a separate operational snapshot and are not included in the historical hypothesis test.

**Historical analysis period:** July 1, 2021 through June 30, 2026  
**Historical records:** 29,646  
**Current/open snapshot records:** 306

The analysis uses descriptive statistics, four visual models, and a chi-square test of independence to evaluate whether the staffing-demand family of ICM-relevant opportunities varies by fiscal quarter.

## Research Question

Do the relative frequencies of two ICM staffing-demand families—Technology Delivery and Advisory, Assurance & Change—differ across California fiscal quarters?

- **Null hypothesis (H0):** Staffing-demand family and fiscal quarter are independent.
- **Alternative hypothesis (H1):** Staffing-demand family and fiscal quarter are associated.

## Key Findings

- The five-year historical dataset contains 29,646 procurement records.
- Transparent title-based rules identified 176 ICM-relevant opportunities.
- Technology Delivery represented 133 of the 176 relevant opportunities (75.6%).
- The chi-square test did not find a statistically significant relationship between staffing-demand family and fiscal quarter: χ²(3) = 0.950, p = 0.813.
- Cramér's V was 0.073, indicating a very small observed association.
- The practical result supports maintaining core software, systems-integration, and data capacity rather than making large quarter-specific staffing changes from this evidence alone.

## Repository Structure

```text
.
├── analysis.ipynb
├── california_public_procurement_2021_2026.csv
├── README.md
├── requirements.txt
├── Statistical_Analysis_Report.pdf
├── module_summary.pdf
├── Statistical_Analysis_Report.docx
├── SUBMISSION_CHECKLIST.md
├── data/
│   ├── raw/
│   │   ├── California 5 Year Historical Bids.xls
│   │   ├── California Current Bids.xls
│   │   ├── El Dorado County - All.csv
│   │   └── Sacramento - All.csv
│   └── processed/
│       ├── analysis_summary.json
│       ├── california_public_procurement_2021_2026.csv
│       ├── classification_audit_sample.csv
│       ├── current_public_procurement_snapshot.csv
│       ├── data_dictionary.csv
│       └── icm_relevant_historical_bids.csv
└── figures/
    ├── figure_1_monthly_icm_relevant_bids.png
    ├── figure_2_relevant_rate_by_jurisdiction.png
    ├── figure_3_staffing_family_by_quarter.png
    └── figure_4_service_category_counts.png
```

## Data Sources

- California Cal eProcure: https://caleprocure.ca.gov/
- County of El Dorado PlanetBids: https://vendors.planetbids.com/portal/48157/bo/bo-search
- City of Sacramento PlanetBids: https://vendors.planetbids.com/portal/15300/bo/bo-search

The original source exports are preserved under `data/raw`. The notebook standardizes common fields, normalizes the analysis period, derives fiscal periods and analytical classifications, and writes reproducible outputs under `data/processed`.

## Reproducing the Analysis

1. Clone or download this repository.
2. Use Python 3.13 (the final notebook was validated with Python 3.13.5).
3. Create and activate a virtual environment.
4. Install the project-specific frozen environment:

   ```bash
   python -m pip install -r requirements.txt
   ```

5. Start Jupyter Notebook or JupyterLab from the repository root.
6. Open `analysis.ipynb`.
7. Restart the kernel and run all cells from top to bottom.

The notebook uses relative paths. It expects the four original exports to remain in `data/raw`. Executing the notebook recreates the processed datasets and figures.

## Analytical Workflow

The notebook performs the following steps:

1. Imports and reproducibility settings
2. Data ingestion and schema verification
3. Cross-source field standardization
4. Five-year date normalization
5. Missingness, duplicate, and source-coverage checks
6. Deterministic ICM relevance and service-category classification
7. Descriptive statistics
8. Four visual models and explicit comparison
9. Chi-square assumption checks, test execution, and effect-size calculation
10. Current-opportunity snapshot
11. Export and validation of reproducible outputs

## Limitations

The title-based relevance classification is deliberately conservative but cannot replace review of full solicitation documents. Bid counts do not measure contract value, labor hours, likelihood of award, or project start date. The three portals also differ in scope, record retention, status terminology, and agency coverage. Results should therefore be treated as directional workforce-planning evidence rather than a precise staffing forecast.

## Academic Sources

The statistical report cites the required peer-reviewed article on systematic initial data analysis and additional peer-reviewed methodological sources. Full APA references are provided in `Statistical_Analysis_Report.pdf` and `module_summary.pdf`.

## GitHub Workflow

The repository was developed on a `development` branch and merged into `main` through a pull request. The repository is available at https://github.com/icmsol/Capstone-project-2-statistical-analysis.
