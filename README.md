# NUNES Catalogue Studio 📐✨

[![Live Production](https://img.shields.io/badge/Live%20Demo-Vercel%20Production-blue?style=for-the-badge&logo=vercel)](https://nunes-catalogue-studio-live.vercel.app/)
[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Framework-Flask%20Serverless-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![ReportLab](https://img.shields.io/badge/PDF%20Engine-ReportLab%204.2-EC1C24?style=for-the-badge)](https://www.reportlab.com/)
[![Gemini AI](https://img.shields.io/badge/AI%20Engine-Google%20Gemini%202.5-4285F4?style=for-the-badge&logo=google)](https://aistudio.google.com/)

> **Enterprise Metrology Catalogue Publishing Engine & Intelligent Document Ingestion Platform.**
> Automatically extracts specifications from spreadsheets, technical datasheets, Word docs, and scanned PDFs, enriches content via Google Gemini AI, and renders certified, publication-grade 2-page A4 catalogues and multi-product mini catalogues.

---

## 🌐 Live Application

Explore the live production deployment running on Vercel:
**[https://nunes-catalogue-studio-live.vercel.app/](https://nunes-catalogue-studio-live.vercel.app/)**

---

## 🎯 Highlights & Core Capabilities

### 1. 📂 Universal Multi-Format Document Ingestion Engine
- **Excel (`.xlsx`, `.xls`)**: Parses multi-sheet workbooks, detects arbitrary `Parameter : Value` tables, strips binary XML internals, and handles merged cells without text corruption.
- **Word (`.docx`)**: Extracts structured tables, bullet points, technical descriptions, and model numbers.
- **PDF Datasheets**: Dual-layer text extraction with OCR fallback for scanned spec sheets.
- **Images (`.png`, `.jpg`, `.webp`)**: Automated studio background removal isolating product hardware on clean white backdrops.
- **CSV / TXT / JSON**: Safe delimiter detection and schema-free specification parsing.

### 2. 🖨️ Precision Two-Page Metrology PDF Engine
- **Strict 2-Page A4 Reference Compliance**: Implements the official NUNES corporate design hierarchy (Magenta `#AC145A`, Slate `#536172`, Dark Navy `#1C2430`).
- **Dynamic Overflow Balancing**: Auto-regulates font size, leading, and paragraph spacing for 150–200 word descriptions so catalogues never overflow onto Page 3.
- **Multi-Product Mini Catalogues**: Automatically groups related instruments with buyer-intent keyword matrices.

### 3. 🤖 AI Metrology Enrichment (Google Gemini 2.5 Flash)
- **Controlled Generation**: Generates 150–200 word metrological descriptions focusing on operating principles, sensor mechanics, and calibration standards.
- **Zero Hallucination Rule**: Strictly preserves confirmed numbers, voltages, and measurement ranges; unverified numbers are never fabricated.
- **Rule-Based Verified Fallback**: Offline fallback engine operates seamlessly when API keys are absent.

### 4. ⚡ Bulk Product List Automation & Cloud Packaging
- **One-Click Batch Bundling**: Processes lists of products or source evidence, generates individual Full PDFs, compiles the combined Mini PDF, and packages everything into a downloadable ZIP with `BATCH_REPORT.csv`.
- **In-Browser Multi-File Queue**: Drag and drop multiple documents simultaneously with per-file progress tracking.

---

## 🏗️ Architecture & Technology Stack

```
                              ┌──────────────────────────────────────────────┐
                              │        Modern Web UX (HTML5 / Vanilla JS)    │
                              │  - Drag & Drop Multi-File Upload Queue       │
                              │  - Two-Column Spec Editor & TSV / Pipe Paste │
                              │  - Live Inline PDF Previewer & Word/Excel    │
                              └──────────────────────┬───────────────────────┘
                                                     │ HTTP JSON / REST
                                                     ▼
┌────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   Flask Serverless Runtime (Vercel)                                │
│                                                                                                    │
│  ┌───────────────────────┐   ┌───────────────────────┐   ┌──────────────────────────────────────┐  │
│  │ Ingestion Pipeline    │   │ AI Content Service    │   │ ReportLab Rendering Engine           │  │
│  │ - openpyxl (Excel)    │   │ - Gemini 2.5 Flash    │   │ - template_layout.py (2-page A4)     │  │
│  │ - python-docx (Word)  │   │ - OpenAI gpt-4o-mini  │   │ - generator.py (Mini PDF matrix)     │  │
│  │ - pypdf / Pillow      │   │ - Rule-based Metrology│   │ - Pillow Cutout Studio               │  │
│  └───────────────────────┘   └───────────────────────┘   └──────────────────────────────────────┘  │
└────────────────────────────────────────────────────┬───────────────────────────────────────────────┘
                                                     │
                                                     ▼
                              ┌──────────────────────────────────────────────┐
                              │                 Output Formats               │
                              │  - Certified 2-Page Full PDF (Print Ready)   │
                              │  - Multi-Product Mini Catalogue PDF          │
                              │  - Editable Word Datasheet (.docx)           │
                              │  - Structured Spec Spreadsheet (.xlsx)       │
                              │  - Cloud ZIP Bundle with CSV Audit Report    │
                              └──────────────────────────────────────────────┘
```

---

## 📡 REST API Reference

| Endpoint | Method | Description |
|---|---|---|
| `/` | `GET` | Interactive Catalogue Studio Web Application |
| `/api/health` | `GET` | Health status and connected AI engine verification |
| `/api/config` | `GET` | Server mode and configuration capabilities |
| `/api/catalogue/upload-auto-generate` | `POST` | Upload file (`.xlsx`, `.docx`, `.pdf`, `.png`), extract specs, and return PDFs |
| `/api/preview` | `POST` | Render and stream real-time inline 2-page PDF |
| `/api/export/docx` | `POST` | Export formatted Microsoft Word `.docx` datasheet |
| `/api/export/excel` | `POST` | Export structured Microsoft Excel `.xlsx` specification table |
| `/api/product/research` | `POST` | Search product images and technical evidence from public sources |
| `/api/catalogue/enrich` | `POST` | Generate 150–200 word description + 8–10 key feature bullets |
| `/api/ai/draft` | `POST` | AI-assisted product drafting from unstructured raw text |
| `/api/catalogue/batch/prepare` | `POST` | Prepare and research single items for batch catalogue automation |
| `/api/catalogue/full-batch` | `POST` | Build downloadable ZIP of multiple Full PDFs + `BATCH_REPORT.csv` |
| `/api/catalogue/instant-cloud` | `POST` | Bundle Full PDFs, Mini PDF, and verification audit report into a ZIP |
| `/api/remove-background` | `POST` | Studio cutout background removal for product hardware images |

---

## 🚀 Quickstart & Local Installation

### Prerequisites
- Python 3.10+ (Recommended: Python 3.12)
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/nunes-catalogue-studio.git
cd nunes-catalogue-studio
```

### 2. Set Up Virtual Environment
```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
Copy the example environment configuration:
```bash
cp .env.example .env
```
Edit `.env` and set your Google Gemini API key:
```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### 5. Run the Local Development Server
```bash
python webapp.py
```
Open your browser at **`http://127.0.0.1:5000`**.

---

## 🧪 Automated Testing & Verification

Run the full local test suite (tests file extractors, PDF layouts, and API routes):
```bash
python test_suite.py
python test_workflow_endpoints.py
```

Run live production end-to-end verification against the deployed domain:
```bash
python test_live_production.py
```

---

## ☁️ Deployment to Vercel

This repository is optimized for one-click serverless deployment on Vercel:

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy directly
vercel deploy --prod
```

Configure your environment variables in the Vercel Dashboard under **Project Settings > Environment Variables**:
- `GEMINI_API_KEY`: Your Google Gemini API Key
- `NUNES_ADMIN_PASSWORD`: Secret admin key for protected exports

---

## 📄 License & Attribution

Developed for **NUNES Instruments / VTech Metrology**.  
Distributed under the **MIT License**. See `LICENSE` for details.

---

## 🌐 Complete Live Run & CI/CD Verification (24 Repositories)

Official production verification matrix for [Abishek Pranav G V](https://abishekpranavgv.github.io/abishekpranavportfolio/) ecosystem:

| # | Repository | Tech Stack & Workflow | Status | Live Run Link | Live App / Pages URL |
|---|---|---|:---:|:---:|:---:|
| 1 | [abishekpranavportfolio](https://github.com/AbishekPranavGV/abishekpranavportfolio) | TypeScript / React / Vite CI & Pages Deploy | ✅ Success | [Run #39437493630](https://github.com/AbishekPranavGV/abishekpranavportfolio/actions/runs/39437493630) | [abishekpranavgv.github.io/abishekpranavportfolio](https://abishekpranavgv.github.io/abishekpranavportfolio/) |
| 2 | [Retail-Sales-Performance-Predictive-Analytics](https://github.com/AbishekPranavGV/Retail-Sales-Performance-Predictive-Analytics) | Executive Dashboard & Pages Deploy | ✅ Success | [Run #39437771618](https://github.com/AbishekPranavGV/Retail-Sales-Performance-Predictive-Analytics/actions/runs/39437771618) | [abishekpranavgv.github.io/Retail-Sales-Performance-Predictive-Analytics](https://abishekpranavgv.github.io/Retail-Sales-Performance-Predictive-Analytics/) |
| 3 | [NICMS-SriLanka-Strategic-Blueprint](https://github.com/AbishekPranavGV/NICMS-SriLanka-Strategic-Blueprint) | Static Site Verification & Pages Deploy | ✅ Success | [Run #39437769957](https://github.com/AbishekPranavGV/NICMS-SriLanka-Strategic-Blueprint/actions/runs/39437769957) | [abishekpranavgv.github.io/NICMS-SriLanka-Strategic-Blueprint](https://abishekpranavgv.github.io/NICMS-SriLanka-Strategic-Blueprint/) |
| 4 | [social-command-center](https://github.com/AbishekPranavGV/social-command-center) | Node.js 20 / Next.js Syntax & CI Validation | ✅ Success | [Run #39438319857](https://github.com/AbishekPranavGV/social-command-center/actions/runs/39438319857) | [nunes-social-post-machine-mu.vercel.app](https://nunes-social-post-machine-mu.vercel.app) |
| 5 | [IndiaMART-AI-Content-Catalog-Generator](https://github.com/AbishekPranavGV/IndiaMART-AI-Content-Catalog-Generator) | Next.js & Automation Bundle Validation | ✅ Success | [Run #39438327386](https://github.com/AbishekPranavGV/IndiaMART-AI-Content-Catalog-Generator/actions/runs/39438327386) | [nunes-social-post-machine-mu.vercel.app](https://nunes-social-post-machine-mu.vercel.app) |
| 6 | [MedX](https://github.com/AbishekPranavGV/MedX) | Python 3.11 Microservices & Endpoint CI | ✅ Success | [Run #39437852044](https://github.com/AbishekPranavGV/MedX/actions/runs/39437852044) | [nunes-catalogue-studio-live.vercel.app](https://nunes-catalogue-studio-live.vercel.app/) |
| 7 | [Streamlit](https://github.com/AbishekPranavGV/Streamlit) | Streamlit Requirements & App Validation | ✅ Success | [Run #39437832596](https://github.com/AbishekPranavGV/Streamlit/actions/runs/39437832596) | [blank-app-template.streamlit.app](https://blank-app-template.streamlit.app/) |
| 8 | [Climate-Impact-ESG-Dashboard](https://github.com/AbishekPranavGV/Climate-Impact-ESG-Dashboard) | Real-time ESG Notebook & Engine CI | ✅ Success | [Run #39437788309](https://github.com/AbishekPranavGV/Climate-Impact-ESG-Dashboard/actions/runs/39437788309) | — |
| 9 | [COVID-19-Global-Forecasting-Predictive-Analysis](https://github.com/AbishekPranavGV/COVID-19-Global-Forecasting-Predictive-Analysis) | Time-Series Forecasting Notebook CI | ✅ Success | [Run #39437782830](https://github.com/AbishekPranavGV/COVID-19-Global-Forecasting-Predictive-Analysis/actions/runs/39437782830) | — |
| 10 | [Customer-Churn-Decision-Analysis](https://github.com/AbishekPranavGV/Customer-Churn-Decision-Analysis) | Decision Analysis & Case Study CI | ✅ Success | [Run #39437795502](https://github.com/AbishekPranavGV/Customer-Churn-Decision-Analysis/actions/runs/39437795502) | — |
| 11 | [E-commerce-Recommendation-Engine](https://github.com/AbishekPranavGV/E-commerce-Recommendation-Engine) | Recommendation Model & CSV Dataset CI | ✅ Success | [Run #39437803215](https://github.com/AbishekPranavGV/E-commerce-Recommendation-Engine/actions/runs/39437803215) | — |
| 12 | [Facedetection](https://github.com/AbishekPranavGV/Facedetection) | OpenCV Cascades & Classifier Python CI | ✅ Success | [Run #39437808536](https://github.com/AbishekPranavGV/Facedetection/actions/runs/39437808536) | — |
| 13 | [Movie_recommendation_using_emotion](https://github.com/AbishekPranavGV/Movie_recommendation_using_emotion) | Emotion Recommender & Streamlit App CI | ✅ Success | [Run #39437816270](https://github.com/AbishekPranavGV/Movie_recommendation_using_emotion/actions/runs/39437816270) | — |
| 14 | [Stock-Price-Prediction-using-ARIMA](https://github.com/AbishekPranavGV/Stock-Price-Prediction-using-ARIMA) | ARIMA & LSTM Model Artifacts CI | ✅ Success | [Run #39437826761](https://github.com/AbishekPranavGV/Stock-Price-Prediction-using-ARIMA/actions/runs/39437826761) | — |
| 15 | [Sentimental-analysis-of-News-Headlines](https://github.com/AbishekPranavGV/Sentimental-analysis-of-News-Headlines) | NLP Sentiment Analysis Notebook CI | ✅ Success | [Run #39436975960](https://github.com/AbishekPranavGV/Sentimental-analysis-of-News-Headlines/actions/runs/39436975960) | — |
| 16 | [Autonomous-System-Temp-Cleaner](https://github.com/AbishekPranavGV/Autonomous-System-Temp-Cleaner) | Windows Automation & Cleaner Batch CI | ✅ Success | [Run #39437859122](https://github.com/AbishekPranavGV/Autonomous-System-Temp-Cleaner/actions/runs/39437859122) | — |
| 17 | [Crm](https://github.com/AbishekPranavGV/Crm) | AI CRM Skill Bundle & Preview Scripts CI | ✅ Success | [Run #39437863792](https://github.com/AbishekPranavGV/Crm/actions/runs/39437863792) | — |
| 18 | [drive-file-index](https://github.com/AbishekPranavGV/drive-file-index) | Google Drive Indexer Distribution CI | ✅ Success | [Run #39437872721](https://github.com/AbishekPranavGV/drive-file-index/actions/runs/39437872721) | — |
| 19 | [Multi-Account-Gmail-Inbox-Hygiene-Agent](https://github.com/AbishekPranavGV/Multi-Account-Gmail-Inbox-Hygiene-Agent) | Multi-Account Gmail Agent Bundle CI | ✅ Success | [Run #39437877580](https://github.com/AbishekPranavGV/Multi-Account-Gmail-Inbox-Hygiene-Agent/actions/runs/39437877580) | — |
| 20 | [NICMS-SriLanka-Strategic-Blueprint_Project](https://github.com/AbishekPranavGV/NICMS-SriLanka-Strategic-Blueprint_Project) | Project Blueprint Specs & Architecture CI | ✅ Success | [Run #39437882917](https://github.com/AbishekPranavGV/NICMS-SriLanka-Strategic-Blueprint_Project/actions/runs/39437882917) | — |
| 21 | [NUNES-Local-AI-Marketing-Starter](https://github.com/AbishekPranavGV/NUNES-Local-AI-Marketing-Starter) | Local AI Marketing Starter Bundle CI | ✅ Success | [Run #39437889129](https://github.com/AbishekPranavGV/NUNES-Local-AI-Marketing-Starter/actions/runs/39437889129) | — |
| 22 | [Smart-Brochure-to-Catalog-Converter](https://github.com/AbishekPranavGV/Smart-Brochure-to-Catalog-Converter) | PDF Catalog Converter Specification CI | ✅ Success | [Run #39437897042](https://github.com/AbishekPranavGV/Smart-Brochure-to-Catalog-Converter/actions/runs/39437897042) | — |
| 23 | [Smart-Price-Master-Catalog-Generator](https://github.com/AbishekPranavGV/Smart-Price-Master-Catalog-Generator) | PriceMaster Multi-OS Package CI | ✅ Success | [Run #39437902153](https://github.com/AbishekPranavGV/Smart-Price-Master-Catalog-Generator/actions/runs/39437902153) | — |
| 24 | [SocmedX](https://github.com/AbishekPranavGV/SocmedX) | Social Command Center Portfolio Bundle CI | ✅ Success | [Run #39437907375](https://github.com/AbishekPranavGV/SocmedX/actions/runs/39437907375) | — |

*Maintained by [Abishek Pranav G V](https://abishekpranavgv.github.io/abishekpranavportfolio/) · Business Analyst & Data/AI Automation Specialist*
