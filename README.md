# 🌍 Climate-Smart AI Business Intelligence Analyst

**BigQuery AI Competition – Approach 1: The AI Architect**

## Overview

A production-ready climate risk analytics system that turns simple business + location context into **executive decisions, live KPIs, and 2025 forecasts**—all **inside BigQuery**. It executes **7/7 BigQuery AI functions** (with a safe fallback for `AI.GENERATE_TABLE`) and uses **BQML ARIMA+** for time-series forecasting.

**Scope analyzed:** 5 companies • 5 locations • **$390M** assets • **2,900** employees  
**Dataset:** `climate_risk_analytics` (US)

---

## 🎯 Problem Solved

- Executives lack clear, quantified views of **site-level climate risk** (heat/flood/storm).  
- Analytic teams spend **25+ hours/week** on manual reports; insights arrive too late.  
- Climate exposure isn’t linked to **financial impact** or **ROI** of adaptation.  
- Forecasts and decisions aren’t **auditable** or **repeatable**.

---

## 💡 Solution

A **SQL-first** system on BigQuery that automatically:
- Generates **executive summaries** and **structured risk profiles** per location.  
- Produces **yes/no decisions**, **numeric scores**, and **int** estimates from prompts.  
- Trains **ARIMA_PLUS** models to forecast **extreme-heat days** and **cost impacts**.  
- Publishes **live executive KPIs** via a **materialized view (MV-safe pattern)**.  
- Logs **method (AI/BQML/FALLBACK), confidence, cost, and latency** for auditability.

**BigQuery AI used:**  
`ML.GENERATE_TEXT`, `AI.GENERATE`, `AI.GENERATE_BOOL`, `AI.GENERATE_DOUBLE`, `AI.GENERATE_INT`, `AI.GENERATE_TABLE` *(fallback path)*, `AI.FORECAST` *(via BQML `ML.FORECAST`)*

---

## 📊 Key Results

| Metric | Result |
|---|---|
| Portfolio Risk Score | **36.7 / 100** |
| High-Risk Locations | **3 / 5** |
| Estimated Annual Climate Loss | **$33.5M** |
| 10-Year Potential Savings | **$251M** (75% loss reduction) |
| Adaptation ROI | **~1,675%** |
| Forecast Confidence | **~0.80** (Phoenix & Miami) |
| AI Functions Operational | **7 / 7** *(table uses labeled fallback when model arg required)* |

**2025 Forecasts**  
• **Phoenix:** **170** extreme-heat days → **HIGH** risk, est. cost **$340k**  
• **Miami:** **115** extreme-heat days → **MEDIUM** risk, est. cost **$230k**

---

## 🏗️ Architecture

Seed Business & Location Data (assets, employees, exposure)
↓
Generative SQL (ML.GENERATE_TEXT / AI.GENERATE / BOOL / DOUBLE / INT)
↓
BQML Forecasting (ARIMA_PLUS via ML.FORECAST → 2025 extreme-heat days & costs)
↓
MV-Safe KPIs (single base table → exec_climate_kpis materialized view)
↓
Audit & Observability (climate_findings: method, confidence, cost, latency)

yaml
Skopiuj kod

**MV pattern:** one **base table** (`portfolio_base`) → **simple expressions only** in MV (`exec_climate_kpis`) to satisfy BigQuery MV constraints.

---

## 🚀 Features

### 1) Executive Climate Reports (per company)
- `ML.GENERATE_TEXT` creates concise, board-ready summaries with risks & mitigations.

### 2) Structured Risk Profiles
- `AI.GENERATE` returns **JSON** with `flood_risk`, `heat_risk`, `operational_impact (1–10)`, `primary_concern`.

### 3) Decision & Scoring Guardrails
- `AI.GENERATE_BOOL` → evacuation / investment-safe / ESG-compliant / act-now  
- `AI.GENERATE_DOUBLE` → 0–100 risk and impact scores  
- `AI.GENERATE_INT` → downtime days, employees at risk, competitive ranking

### 4) Forecasts You Can Plan On
- BQML **ARIMA_PLUS** forecasts **extreme-heat days** & cost impact for 2025.  
- Confidence, upper/lower bounds, and **risk categorization** per location.

### 5) Live Executive KPIs (MV)
- Risk category, loss estimate, risk score component, critical infra flags.  
- **Query-ready** for dashboards (Looker Studio, Connected Sheets, etc.).

### 6) Full Observability
- `climate_findings` tracks **AI/BQML/FALLBACK**, confidence, processing time, and cost per function.

---

## 💻 Technology Stack

- **BigQuery SQL + BigQuery AI**: `ML.GENERATE_TEXT`, `AI.GENERATE*`, `ML.FORECAST`  
- **BQML**: `ARIMA_PLUS`  
- **Python / Kaggle**: orchestration & prints, secrets handling  
- **Governance**: metadata logging, explicit labeled fallbacks

---

## 🛠️ Setup & Installation

### Prerequisites
- GCP project with **BigQuery** and **Vertex AI** enabled  
- A **BigQuery connection** to Vertex AI (e.g., `us.vertex_ai_connection`)  
- Kaggle account (to run the notebook)

### Quick Start
1. Open `climate_smart_business_risk_assessment.ipynb` in Kaggle.  
2. In **Kaggle Secrets**, add `GCP_SA_KEY` (service account JSON).  
3. Set your project/config and **Run All**.

### Configuration
```python
PROJECT_ID   = "your-project-id"
DATASET_ID   = "climate_risk_analytics"
LOCATION     = "us"
CONNECTION_ID= "vertex_ai_connection"  # must exist in your project/region
MODEL_NAME   = "gemini_climate_model"  # optional alias used in prompts

# Kaggle secrets
from kaggle_secrets import UserSecretsClient
from google.oauth2 import service_account
user_secrets = UserSecretsClient()
creds_info   = json.loads(user_secrets.get_secret("GCP_SA_KEY"))
credentials  = service_account.Credentials.from_service_account_info(creds_info)
Note: AI.GENERATE_TABLE requires a MODEL argument in current BigQuery.
The notebook includes a transparent fallback (clearly labeled) so pipelines don’t break.

📈 Business Impact
Quantified Benefits (portfolio example)
Annual climate loss: $33.5M baseline

10-yr savings: $251M with 75% reduction

Adaptation ROI: ~1,675% (quick wins ~600–680% ROI, ~2-month payback)

Ops time savings: 90%+ vs. manual reporting

Day-1 Actions for Executives
Fund cooling systems & employee safety first (fastest ROI).

Use yes/no guardrails for expansion & ESG decisions.

Track risk shifts & loss estimates via the MV.

🏆 Competition Readiness
Approach 1: The AI Architect — implemented end-to-end

✅ 7/7 AI functions exercised (table generation with labeled fallback)

✅ BQML ARIMA+ forecasting with confidence

✅ MV-safe KPIs + audit trail

✅ Clean, reproducible notebook & documentation

📂 Files Structure
bash
Skopiuj kod
├── climate_smart_business_risk_assessment.ipynb  # Main notebook
├── README.md                                     # This file
├── requirements.txt                              # Dependencies (Kaggle friendly)
├── results/
│   ├── exec_climate_kpis.csv
│   ├── climate_forecasts_2025.csv
│   └── climate_findings.csv
└── docs/
    ├── architecture_diagram.png
    └── mv_pattern_and_governance.md
🔗 Demo Links
🖥️ Live Kaggle Notebook: [Add your link]

💻 GitHub Repository: [Add your link]

📄 Write-up / Article: [Add your Medium link]

🤝 Contributing
Built for the BigQuery AI – Building the Future of Data competition.
Fork it to adapt for your own climate/asset portfolio.

📄 License
MIT License — see LICENSE.

👨‍💻 Author
Created by Martin Szerment — September 2025
Approach 1: The AI Architect — climate-smart business intelligence
