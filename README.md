📈 Job Demand and Sector Analytics

An evidence-based analytical system for examining employment indicators, occupational demand, and sector dynamics across reporting periods and regional geographies.

Python 3.11+
Streamlit 1.30+
Plotly 5.18+
Tests-Passing
License: MIT

1. Project Overview

Job Demand and Sector Analytics is an end-to-end Python data analytics platform and interactive web dashboard designed to evaluate labour market trends, sectoral strengths, occupational demands, and district-level disparities across Karnataka and national benchmarks.

The application adheres to strict empirical validation and statistical guardrails:

No Inappropriate Indicator Mixing: Administrative vacancy counts, household survey estimates, factory worker counts, and digital job postings have distinct mathematical definitions and are never added together.
Geographic Precision: District-level evaluations cover all 31 administrative districts in Karnataka using verified Directorate of Economics & Statistics (DES) factory returns.
Traceable Provenance: Every metric traces directly to official administrative bodies (DGE, DES Karnataka, Labour Bureau, MoSPI NSSO).
2. Problem Statement

Public labour market intelligence is often published in fragmented gazettes, surveys, and registers with conflicting metrics:

Conflating Demand and Employment: Job vacancies are frequently mischaracterized as total employment numbers.
Tech-Skewed Proxies: Online job advertisement counts often over-represent digital and metropolitan jobs while under-representing agriculture and the unorganized sector.
Obscured Regional Disparities: Statewide aggregation masks high geographic concentration in economic centers like Bengaluru Urban compared to other districts.
Unsound Growth Rates: Period-over-period growth is often reported without checking for baseline changes or methodological shifts.

This project delivers a standardized schema, rigorous automated data validation, and an interactive decision-support dashboard to overcome these challenges.

3. Project Objectives
Sectoral Strength: Identify leading sectors by employment volumes, growth rates, and notified vacancies.
Occupational Demand: Determine top occupations using National Classification of Occupations (NCO) groupings.
Geographic Concentration: Measure regional disparities between Bengaluru Urban and Karnataka's other 30 administrative districts.
Longitudinal Trends: Calculate period-over-period changes and Compound Annual Growth Rates (CAGR) with baseline validation.
Market Concentration (
𝐶
𝑅
𝑛
CR
n
	​

): Quantify occupational and sectoral concentration ratios (
𝐶
𝑅
3
CR
3
	​

, 
𝐶
𝑅
5
CR
5
	​

).
Data Provenance: Maintain transparent links to official public sources.
4. Key Features & Dashboard Pages
Page	Description	Key Indicators & Features
app.py (Overview)	Executive summary & platform KPIs	Key indicator cards, project introduction, source health check, automated executive brief.
1_Sector_Analytics.py	Sectoral breakdown and rankings	Leading sectors by employment and vacancies, sector share distribution, horizontal bar charts.
2_Occupation_Analytics.py	Occupational demand analysis	Top occupations by NCO code, concentration ratios (
𝐶
𝑅
3
CR
3
	​

, 
𝐶
𝑅
5
CR
5
	​

), demand shares.
3_District_Analytics.py	31-district spatial analysis	Bengaluru Urban vs rest-of-Karnataka benchmarking, district ranking table, choropleth/bar maps.
4_Time_Series_and_Growth.py	Temporal evolution & CAGR	Multi-period trendlines, period-over-period growth rates, CAGR calculation engine.
5_Data_Explorer.py	Interactive data grid & export	Multidimensional filtering, search, and direct CSV/Excel data download.
6_Sources_and_Methodology.py	Data provenance register	Methodology documentation, formulas, limitation caveats, official publication links.
5. System Architecture

[ Official Data Sources (CSV / Excel) ] │ - Directorate General of Employment (DGE) │ - Directorate of Economics & Statistics (DES) Karnataka │ - Labour Bureau (QES) │ - MoSPI NSSO (PLFS) │ - Online Job Postings (Recruitment Proxies) ▼ [ Data Loader & Ingestion (src/data_loader.py) ] │ ▼ [ Cleaning & Standardization (src/data_cleaning.py) ] │ - Column alias mapping (snake_case) │ - District name normalization │ - Period & date parsing ▼ [ Taxonomy & Guardrails (src/indicator_classification.py) ] │ - Segregation into independent indicator types ▼ [ Quality Assurance & Validation (src/data_validation.py) ] │ - Boundary checks (non-negative counts, rate 0-100%) │ - Duplicate detection (exact vs dimensional) ▼ [ Unified Analytics Engine ] ├── Core Analytics (src/analytics.py) ├── Growth & CAGR Engine (src/growth_analysis.py) ├── Geographic Benchmarking (src/geographic_analysis.py) ├── Automated Reporting (src/reporting.py) └── Interactive Plotly Visualizations (src/visualisations.py) │ ▼ [ Streamlit Multi-Page Web Dashboard (app.py + pages/*.py) ]

---
## 6. Directory Structure

job-demand-sector-analytics/ ├── app.py # Main application entry point (Overview) ├── requirements.txt # Project dependencies ├── README.md # Project documentation ├── .gitignore # Git ignore definitions ├── conftest.py # Pytest configuration ├── pytest.ini # Test runner settings ├── run.bat # Windows launch script ├── run.sh # Linux/macOS launch script │ ├── config/ │ └── settings.py # App settings, paths, indicator definitions │ ├── data/ │ ├── raw/ # Official raw datasets │ │ ├── dge_vacancies_by_sector.csv │ │ ├── dge_vacancies_by_occupation.csv │ │ ├── karnataka_des_factory_employment.csv │ │ ├── labour_bureau_qes_sectoral.csv │ │ ├── mospi_plfs_sectoral_shares.csv │ │ ├── online_job_postings_tech_karnataka.csv │ │ └── karnataka_employment_compendium.xlsx │ ├── processed/ # Stored clean datasets │ └── README.md # Data schema and provenance register │ ├── src/ │ ├── analytics.py # Aggregation, rankings, concentration │ ├── data_cleaning.py # Schema normalization │ ├── data_loader.py # Multi-format ingestion │ ├── data_validation.py # Quality checks and boundary assertions │ ├── geographic_analysis.py # District disparity calculations │ ├── growth_analysis.py # Growth rate and CAGR calculations │ ├── indicator_classification.py # Indicator definitions and guardrails │ ├── reporting.py # Markdown report generation │ ├── source_registry.py # Official source metadata │ ├── ui_helpers.py # Caching and shared UI components │ └── visualisations.py # Plotly charting functions │ ├── pages/ │ ├── 1_Sector_Analytics.py │ ├── 2_Occupation_Analytics.py │ ├── 3_District_Analytics.py │ ├── 4_Time_Series_and_Growth.py │ ├── 5_Data_Explorer.py │ └── 6_Sources_and_Methodology.py │ ├── reports/ # Presentations, PDF briefs, summaries │ ├── Job_Demand_and_Sector_Analytics_Presentation.pptx │ ├── job_demand_sector_analytics_summary.md │ └── PragyanAI - First Hackathon - FrontEnd,BackEnd-DB-Analytics,GenAI and AgenticAI.pdf │ └── tests/ # Automated unit tests (28 tests) ├── test_analytics.py ├── test_data_cleaning.py ├── test_data_validation.py ├── test_geographic_analysis.py └── test_growth_analysis.py

---
## 7. Installation & Setup
### Prerequisites
- **Python 3.11+** installed ([python.org](https://www.python.org/))
- **Git** installed ([git-scm.com](https://git-scm.com/))
### 1. Clone the Repository
```bash
git clone https://github.com/KSNISHANTH333/Job-Analysis.git
cd Job-Analysis
2. Create and Activate a Virtual Environment
bash
# Windows
python -m venv venv
venv\Scripts\activate
# macOS / Linux
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
bash
pip install -r requirements.txt
8. Running the Application
Option A: Using the Launcher Script (Windows)

Double-click run.bat or run:

cmd
run.bat
Option B: Using Streamlit Directly
bash
streamlit run app.py

Open your browser and navigate to:

http://localhost:8501
9. Running Automated Tests

To run the full suite of 28 unit tests:

bash
python -m pytest

Expected output:

tests/test_analytics.py ......                                           [ 21%]
tests/test_data_cleaning.py ....                                         [ 35%]
tests/test_data_validation.py ......                                     [ 57%]
tests/test_geographic_analysis.py ..                                     [ 64%]
tests/test_growth_analysis.py ..........                                 [100%]
============================= 28 passed in 1.16s ==============================
10. Data Provenance & Methodology
Indicator Classified	Unit	Publishing Body	Description
Actual vacancy count	Postings / Vacancies	Directorate General of Employment (DGE)	Vacancies formally notified under the Employment Exchanges Act.
Employment estimate	Thousands of workers	Labour Bureau (Quarterly Employment Survey)	Establishment-based survey covering 9 non-farm sectors.
Registered factory employment	Number of workers	Directorate of Economics and Statistics (DES) Karnataka	Annual factory inspectorate returns across all 31 Karnataka districts.
Observed job postings (proxy)	Postings count	Online Tech Portals	Digital hiring intent proxy; sensitive to metropolitan tech bias.
11. License

This project is open-source and available under the MIT License.
