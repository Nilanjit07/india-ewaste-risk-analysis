# 🌏 India E-Waste Risk Analysis
### A Data Analytics Portfolio Project | Nilanjit Phulia | IIT Hyderabad

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat-square&logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0?style=flat-square)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8-11557C?style=flat-square)
![Data Source](https://img.shields.io/badge/Data-Official%20Govt%20(data.gov.in)-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## 📌 Problem Statement

> **India is the third-largest generator of e-waste in the world, producing over 1.75 million tonnes annually — yet nearly 57% of it goes unprocessed, leaching toxic materials into soil and water while losing an estimated ₹4,700 crore worth of recoverable resources every year.**

Despite an improving regulatory framework under the E-Waste Management Rules and Extended Producer Responsibility (EPR) mandates, the burden of e-waste is distributed **highly unequally** across Indian states. Some states have developed robust recycling infrastructure, while others — particularly in the North-East and East — have almost no registered recycling capacity and fail to report data consistently to the Central Pollution Control Board (CPCB).

This project asks three core questions:

1. **How has India's e-waste generation and recycling trajectory evolved from 2017 to 2024?**
2. **Which Indian states are most at risk from e-waste mismanagement — and why?**
3. **How does India's recycling performance compare to global peers, and what does it mean for policy?**

Using official parliamentary data from Rajya Sabha sessions and the UN Global E-Waste Monitor 2024, this project builds a **composite State Risk Scorecard** that identifies critical-risk states, detects data anomalies, and delivers actionable policy recommendations — the kind of structured, evidence-based analysis performed by management consulting firms.

---

## 📂 Project Structure

```
india-ewaste-risk-analysis/
│
├── data/
│   ├── India_Ewaste_Dataset_Official.xlsx   ← Compiled multi-source dataset
│   ├── RS_Session_263_AU_670.csv            ← State-wise collection (Official)
│   ├── RS_Session_265_AU_1177.csv           ← National generation & recycled
│   └── RS_Session_266_AU_2384.csv           ← National generation 2019-24
│
├── charts/
│   ├── chart1_generation_trend.png
│   ├── chart2_generation_vs_recycling.png
│   ├── chart3_top_bottom_states.png
│   ├── chart4_yoy_state_change.png
│   ├── chart5_outlier_detection.png
│   ├── chart6_zonewise_analysis.png
│   ├── chart7_global_benchmarking.png
│   ├── chart8_recycling_trajectory.png
│   ├── chart9_risk_scorecard_heatmap.png
│   └── chart10_risk_summary.png
│
├── India_Ewaste_Risk_Analysis.ipynb         ← Main Colab Notebook
└── README.md
```

---

## 🗃️ Data Sources

| Source | Dataset | Coverage | Type |
|---|---|---|---|
| Rajya Sabha Session 263 / AU-670 | State/UT-wise e-waste collected & processed | 30 States, 2020-21 & 2021-22 | **Official Govt CSV** |
| Rajya Sabha Session 265 / AU-1177 | National generation & recycling volumes | 2021-22 to 2023-24 | **Official Govt CSV** |
| Rajya Sabha Session 266 / AU-2384 | National e-waste generation | 2019-20 to 2023-24 | **Official Govt CSV** |
| CPCB Annual Reports | Baseline national generation & recycling | 2017-18 to 2018-19 | Secondary |
| Global E-Waste Monitor 2024 (ITU/UNITAR) | Country-wise generation, recycling, per-capita | 12 countries, 2022 | International |

> All Indian government CSVs sourced directly from [data.gov.in](https://data.gov.in) — the official Open Government Data platform.

---

## 🔬 Methodology

### Phase 1 — Data Collection & Cleaning
- Loaded 3 official government CSVs + 1 international dataset
- Handled missing values (`NA` — states that did not report to CPCB)
- Merged sheets into a single analysis-ready Excel workbook
- Preserved NA flags as analytical signals (not imputed) — unreported data itself indicates governance gaps

### Phase 2 — National Trend Analysis
- Year-wise generation trend with YoY growth overlay (2017–2024)
- Generation vs. recycling gap analysis with recycling rate trajectory
- Key metric: recycling rate improved from **9.8% (2017-18) → 43.5% (2023-24)**

### Phase 3 — State-wise Analysis
- Top 10 and Bottom 10 states by collection volume (2021-22)
- YoY change analysis — growth vs. decline by state
- Statistical outlier detection using **Z-Score method** (threshold: |Z| > 1.5)
- Key anomaly: Chhattisgarh showed a **16x collection spike** (258T → 4,167T)

### Phase 4 — Zone-wise Risk Aggregation
- Grouped 30 states into 7 zones (North, South, East, West, Central, NE, Island)
- Calculated average collection per state by zone
- Assigned zone-level risk categories based on volume and reporting compliance

### Phase 5 — Global Benchmarking
- Compared India's recycling rate against 11 countries + world average
- Bubble chart: per-capita e-waste vs recycling rate (bubble = total volume)
- India's recycling trajectory plotted against EU average (75%) and world average (22.3%)

### Phase 6 — Composite State Risk Scorecard
Built a **100-point risk scoring framework** across 3 components:

| Component | Max Points | Logic |
|---|---|---|
| Collection Volume Score | 40 pts | Lower collection = higher risk |
| YoY Growth Score | 30 pts | Negative growth or missing data = higher risk |
| Data Reporting Score | 30 pts | NA in either year = governance risk |

States scored and categorised into: **Critical / High / Medium / Low**

---

## 📊 Key Findings

### 🇮🇳 National Trends
- India's e-waste generation **grew 147%** from 2017-18 to 2023-24
- Recycling rate improved significantly: **9.8% → 43.5%** over 7 years
- Despite improvement, **~990,000 tonnes went unprocessed** in 2023-24
- Estimated recoverable value lost: **~₹4,700 crore annually** (based on UN $57/kg estimate)

### 🗺️ State-wise Findings
- **Haryana** was the top collector in 2021-22 (245,015T) despite having no 2020-21 data
- **Chhattisgarh** showed a statistically anomalous 16x spike — likely driven by sudden EPR compliance
- **Gujarat and Karnataka** showed sharp YoY declines — possibly due to high 2020-21 base
- **4 states** had missing data in at least one year — a governance red flag

### 🌍 Global Context
- India ranks **3rd globally** in total e-waste volume (behind China and USA)
- India's recycling rate (43.5%) now **exceeds the world average** (22.3%)
- Still **31.5 percentage points behind** the EU average (~75%)
- India's per-capita generation (1.1 kg) is far below the global average (7.8 kg) — but will rise sharply with economic growth

---

## 💡 Policy Recommendations

1. **Priority Infrastructure** — Establish CPCB-registered recycling centres urgently in Bihar, Jharkhand, and all NE states, which consistently show Critical-risk scores
2. **Mandatory Reporting** — Make annual state-level e-waste reporting to CPCB legally mandatory with penalties for non-compliance
3. **EPR Enforcement** — Strengthen producer EPR targets for consumer electronics — the fastest-growing e-waste category
4. **Informal Sector Formalisation** — The informal recycling sector handles ~70-80% of actual recycling but under environmentally unsafe conditions; licensing and safety training schemes are critical
5. **2030 Target** — Achieve 60% recycling rate by 2030 to align with India's net-zero climate commitments

---

## 🛠️ Tools & Libraries

```python
# Core
pandas      # Data loading, cleaning, aggregation
numpy       # Statistical computations (Z-score, pct_change)

# Visualisation
matplotlib  # Base charting (bar, line, scatter, bubble)
seaborn     # Heatmap (Risk Scorecard), theme styling

# Statistical
scipy.stats # Z-score outlier detection

# Utilities
zipfile     # Packaging output charts
google.colab # File upload/download (Colab environment)
openpyxl    # Excel dataset compilation
```

---

## 🚀 How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `India_Ewaste_Risk_Analysis.ipynb`
3. Upload `India_Ewaste_Dataset_Official.xlsx` when prompted
4. Run all cells sequentially (Runtime → Run All)
5. Download the output ZIP containing all 10 charts

---

## 📈 Charts Generated

| # | Chart | Key Insight |
|---|---|---|
| 1 | Generation Trend (2017–2024) | 147% growth over 7 years |
| 2 | Generation vs Recycling Gap | ~990k T unprocessed in 2023-24 |
| 3 | Top & Bottom States (2021-22) | Haryana leads; Andaman last |
| 4 | YoY State Change | Chhattisgarh +1516%; Gujarat -72% |
| 5 | Outlier Detection (Z-Score) | 3 statistical outliers identified |
| 6 | Zone-wise Risk Analysis | NE & East zones most at risk |
| 7 | Global Benchmarking | India 3rd globally; above world avg |
| 8 | Recycling Trajectory vs World | 31.5 pp gap vs EU remains |
| 9 | Risk Scorecard Heatmap | Full state-level risk breakdown |
| 10 | Risk Summary | % of states in each risk category |

---

## 👤 About the Author

**Nilanjit Phulia**
M.Tech in E-Waste Resource Engineering & Management
Indian Institute of Technology, Hyderabad

- 🔗 [LinkedIn](https://www.linkedin.com/in/nilanjit-phulia)
- 📧 nilanjit.baban07@gmail.com

> This project combines domain expertise in e-waste engineering with data analytics skills to produce a consulting-grade risk assessment — bridging technical knowledge and business insight.

---

## 📄 License

This project is open-source under the [MIT License](LICENSE).
Data sourced from Indian Government (data.gov.in) and ITU/UNITAR — publicly available for research and analysis.

---

*⭐ If you found this project useful, consider starring the repository!*
