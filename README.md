<p align="center">
  <img src="matrix.svg" alt="SINGHAM Matrix Rain" width="100%" />
</p>

<h1 align="center" style="font-size:160px;">
🛡️ SINGHAM
</h1>

<h3 align="center">
Secure Intelligence for Network Guarding, Hazard Analysis & Monitoring
</h3>

<p align="center">
<img src="https://readme-typing-svg.herokuapp.com?font=Orbitron&weight=700&size=24&duration=3000&pause=1200&color=00E6A8&center=true&vCenter=true&width=900&lines=AI-Powered+Cybersecurity+Platform;Detect+Phishing+Emails;Analyze+Malicious+URLs;Scan+Fake+QR+Codes;Identify+Malware+Downloads;Explain+Threats+Using+AI" />
</p>

<p align="center">
<img src="https://img.shields.io/badge/Status-Under%20Development-orange?style=for-the-badge">
<img src="https://img.shields.io/badge/Backend-Flask-blue?style=for-the-badge">
<img src="https://img.shields.io/badge/Frontend-VanillaJS-yellow?style=for-the-badge">
<img src="https://img.shields.io/badge/Machine%20Learning-XGBoost-success?style=for-the-badge">
<img src="https://img.shields.io/badge/License-MIT-red?style=for-the-badge">
</p>

---

# 🚀 Overview

**SINGHAM** is an AI-powered cybersecurity platform designed to help everyday internet users detect and understand digital threats before they become victims.

Instead of relying on multiple disconnected security tools, SINGHAM brings email analysis, malicious URL detection, fake QR code verification, malware detection, and AI-powered explanations into a single intelligent platform.

The goal is to make cybersecurity simple, understandable, and accessible for everyone.

---

# ❗ Problem Statement

Modern cyber attacks have become increasingly sophisticated. Every day, users receive phishing emails, click malicious links, scan fake QR codes, and unknowingly download malware.

Most existing security tools focus on only one threat category, forcing users to switch between multiple services while still lacking a complete understanding of why something is dangerous. For non-technical users, distinguishing legitimate content from malicious content has become extremely difficult.

SINGHAM addresses this challenge by providing one unified platform capable of analyzing multiple cyber threats while explaining every prediction in simple language.

---

# 💡 Solution

SINGHAM combines Machine Learning and Large Language Models to analyze different cybersecurity threats through a single web interface.

Instead of simply labeling something as "Safe" or "Dangerous", the platform also explains **why** the prediction was made using Explainable AI (XAI). Users receive actionable recommendations that help them make safer online decisions while gradually improving their cybersecurity awareness.

---

# ✨ Core Features

### 📧 AI Email Phishing Detection
- Analyze suspicious emails by uploading their text or PDF source.
- Detect phishing attempts using LLM + RAG powered reasoning.
- Explain why an email is dangerous with specific red flags.

### 🌐 Scam URL Detection
- Detect malicious websites and analyze URL structures.
- Perform domain feature analysis using Machine Learning classification.

### 📱 Fake QR Code Detection
- Decode QR codes and validate destination URLs.
- Detect phishing redirections and warn before opening websites.

### 🦠 Malware Detection
- Scan uploaded files and analyze executable PE structures.
- Compare file hashes and detect known malware signatures.

### 🤖 Explainable AI (XAI)
- Transparent reporting on why a threat was flagged.
- Shows which specific indicators were suspicious.
- Provides risk level estimation and actionable recommendations.

---

# 🏗️ System Architecture

```mermaid
flowchart TD
    %% Styling
    classDef userStyle fill:#0f172a,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    classDef frontendStyle fill:#1e293b,stroke:#3b82f6,stroke-width:2px,color:#f8fafc;
    classDef routeStyle fill:#0f172a,stroke:#8b5cf6,stroke-width:2px,color:#f8fafc;
    classDef backendStyle fill:#1e293b,stroke:#10b981,stroke-width:2px,color:#f8fafc;
    classDef modelStyle fill:#0f172a,stroke:#f59e0b,stroke-width:2px,color:#f8fafc;
    classDef dbStyle fill:#111827,stroke:#ec4899,stroke-width:2px,color:#f8fafc;

    %% Nodes
    User([👤 End User]):::userStyle
    
    subgraph Frontend [🎨 User Interface - HTML5 / CSS3 / Vanilla JS]
        Portal[🏠 Home Landing Portal]
        URLDash[🌐 URL Scam Dashboard]
        QRDash[📱 Fake QR Dashboard]
        MalDash[🦠 Malware Dashboard]
        EmailDash[📧 Email Phishing Dashboard]
    end
    class Portal,URLDash,QRDash,MalDash,EmailDash frontendStyle;

    subgraph API [🛣️ Unified API Routes - Flask Backend]
        R_Home["/ (GET)"]
        R_URL["/predict (POST)"]
        R_QR["/predict_qr (POST)"]
        R_Mal["/analyze_malware (POST)"]
        R_Email["/analyze_email (POST)"]
    end
    class R_Home,R_URL,R_QR,R_Mal,R_Email routeStyle;

    subgraph Engine [⚙️ Processing & Analytics Engines]
        URLExt[Extract URL Features]
        MalExt[Extract PE File Features]
        PDFExt[Extract PDF Text]
        RAGEngine[LangChain RAG Engine]
    end
    class URLExt,MalExt,PDFExt,RAGEngine backendStyle;

    subgraph Models [🧠 Models & AI Layer]
        PhishModel[phishing_model.pkl<br/>XGBoost / Random Forest]
        SHAP["SHAP Explainability (XAI)<br/>PhishingExplainer"]
        MalModel[malwareclassifier-V2.pkl<br/>PE File Classifier]
        Gemini[Gemini 3.5 Flash LLM]
    end
    class PhishModel,SHAP,MalModel,Gemini modelStyle;

    subgraph Storage [💾 Databases & Context Storage]
        FAISS[(FAISS Vector Store)]
        SQLite[(SQLite stats.db)]
        KB[knowledge_base.txt]
    end
    class FAISS,SQLite,KB dbStyle;

    %% Connections
    User --> Portal
    Portal --> URLDash & QRDash & MalDash & EmailDash
    
    URLDash --> R_URL
    QRDash --> R_QR
    MalDash --> R_Mal
    EmailDash --> R_Email
    
    R_URL & R_QR --> URLExt
    R_Mal --> MalExt
    R_Email --> PDFExt
    
    URLExt --> PhishModel
    PhishModel --> SHAP
    SHAP --> URLDash & QRDash
    
    MalExt --> MalModel
    MalModel --> MalDash
    
    PDFExt --> RAGEngine
    KB --> RAGEngine
    RAGEngine --> FAISS
    FAISS --> Gemini
    Gemini --> EmailDash
    
    R_QR --> SQLite
```

---

# 🛠️ Technology Stack

| Layer | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5, CSS3, Vanilla JavaScript | Responsive user interface, interactive threat alerts, and dynamic dashboards. |
| **Backend** | Flask, Gunicorn | Lightweight Python web framework and WSGI server for serving APIs and layouts. |
| **Machine Learning** | XGBoost, Random Forest, Scikit-learn | Supervised classification models for predicting phishing URLs and malware. |
| **Explainable AI (XAI)** | SHAP (SHapley Additive exPlanations) | Explains URL classifier predictions by computing the contribution of each feature. |
| **Generative AI** | Gemini 3.5 Flash, LangChain | RAG-based email phishing analysis and natural language explanation generation. |
| **Vector Database** | FAISS | Vector similarity search database used to retrieve documents for email analysis. |
| **Core Libraries** | Pandas, NumPy, PyPDF2, pefile | PE header parsing, data manipulation, and text extraction from PDF files. |
| **VCS & Environments** | Git, GitHub, Virtualenv | Code versioning and isolated execution environments. |

---

# 📂 Project Structure

```text
SINGHAM/
├── backend/                        # Flask backend application
│   ├── ML_model/                   # Machine Learning model binaries
│   │   └── malwareclassifier-V2.pkl # Pre-trained malware classifier model
│   ├── app.py                      # Main Flask application and API route controllers
│   ├── explainability.py           # SHAP explanation calculations for threat analysis
│   ├── feature_extraction_malware.py # Portable Executable (PE) file parsing & feature extractor
│   ├── featureextraction.py        # URL security feature extraction logic
│   ├── knowledge_base.txt          # Reference text/document database for RAG phishing detector
│   ├── phishing_model.pkl          # Pre-trained XGBoost/Random Forest URL scanner model
│   ├── stats.db                    # SQLite database to track system scan metrics
│   └── uploads/                    # Temporary storage directory for uploaded files during scans
├── frontend/                       # User Interface resources
│   ├── static/                     # Static CSS styling & JavaScript logic files
│   │   ├── email/                  # Static assets for the Email Phishing detector
│   │   │   ├── script.js
│   │   │   └── style.css
│   │   ├── fake_qr/                # Static assets for the Fake QR Code scanner
│   │   │   ├── app.js
│   │   │   └── style.css
│   │   └── url_scam/               # Static assets for the Scam URL scanner
│   │       ├── app.js
│   │       └── style.css
│   └── templates/                  # Jinja2 HTML pages served by Flask
│       ├── email_dashboard.html    # Phishing email scan dashboard
│       ├── home.html               # Main landing portal
│       ├── malware_dashboard.html  # Malware scanner upload panel
│       ├── malware_result.html     # Malware analysis result display
│       ├── qr_dashboard.html       # QR scan dashboard
│       └── url_dashboard.html      # URL scan dashboard
├── .env.example                    # Template for configuring environment variables
├── .gitignore                      # Configuration for Git ignored files
├── Licence                         # Project License agreement
├── matrix.svg                      # Custom Matrix digital rain animation SVG for README.md
├── requirements.txt                # Python backend package dependencies
└── README.md                       # Documentation of the project
```

---

# ⚙️ Setup & Installation

Follow these steps to set up and run SINGHAM on your local machine:

### 1. Prerequisites
Ensure you have **Python 3.8+** installed on your system.

### 2. Clone the Repository
Clone the repository and navigate to the project root directory:
```bash
git clone <repository-url>
cd SINGHAM
```

### 3. Create a Virtual Environment
Create and activate an isolated Python virtual environment:
- **On Linux/macOS:**
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```
- **On Windows:**
  ```cmd
  python -m venv venv
  venv\Scripts\activate
  ```

### 4. Install Dependencies
Install all required packages from `requirements.txt`:
```bash
pip install -r requirements.txt
```

### 5. Set Up Environment Variables
The Email Phishing analysis system relies on Google Gemini models. You need to configure a Google Gemini API Key:
1. Copy the `.env.example` file into the `backend/` directory as `.env`:
   ```bash
   cp .env.example backend/.env
   ```
2. Open `backend/.env` in your text editor and set `GEMINI_API_KEY` to your actual API key:
   ```env
   GEMINI_API_KEY=your_actual_gemini_api_key_here
   ```
   > [!TIP]
   > You can get a free API Key from [Google AI Studio](https://aistudio.google.com/).

### 6. Run the Application
1. Navigate to the backend directory:
   ```bash
   cd backend
   ```
2. Launch the Flask development server:
   ```bash
   python app.py
   ```
3. Open your browser and navigate to:
   [http://127.0.0.1:5000/](http://127.0.0.1:5000/)

---

# 🎯 Development Roadmap

- ✅ Project Planning
- ✅ System Design
- ✅ Dataset Collection
- ⏳ Frontend Development & UI Refinement
- ⏳ Backend APIs integration
- ⏳ Unified Email Phishing Detection
- ⏳ Unified URL Scam Detection
- ⏳ Unified QR Scam Detection
- ⏳ Unified Malware Detection
- ⏳ AI Explanation (XAI) Engine
- ⏳ Centralized Threat Report Dashboard
- ⏳ Production Deployment & Docker Support
