# 🤖 HR AI Agent – Multi-Agent FastAPI App 📦

This project is a Python-based FastAPI application that uses multi-agent collaboration to answer questions related to **HR policies** and **Finance** at BMV System Integration (BMVSI). It's built with:

- 🧠 [Agno](https://github.com/agno-agi/agno) agent framework
- 🔮 [Gemini AI](https://deepmind.google/technologies/gemini/) by Google
- ⚡ [FastAPI](https://fastapi.tiangolo.com/)
- ☁️ [Google Drive integration](https://drive.google.com/)

---

## 🚀 Features 

- Multi-agent system: Questions are routed to specialized AI agents (HR or Finance).
- Automatic fallback: If a policy doesn't exist, another agent **sends a suggestion email to HR** recommending new policy creation.
- Google Drive support: Reads policies from `BMVSI_HR_POLICIES` folder in your Google Drive.

---

## 🧰 Prerequisites

- ✅ [Python 3.9+](https://www.python.org/downloads/)
- ✅ Google Cloud Project with:
      - Drive API enabled
      - OAuth credentials
- ✅ Gemini API Key from [Google AI Studio](https://aistudio.google.com/app/apikey)

---

## 🔧 One-Time Google Cloud & Drive Setup

### 1. Create a Google Cloud Project
- Go to: https://console.cloud.google.com/projectcreate
- Name your project (e.g., `HR AI Assistant`)
- Click **Create**

### 2. Configure OAuth Consent Screen
- Go to: https://console.cloud.google.com/auth/overview/create
- Select **External** user type
- Fill out App Info:
  - App Name (e.g., `AI Assistant`)
  - Support Email (e.g., `Your email`)
- Agree to terms and create the app

### 3. Create OAuth Client ID
- Go to: https://console.cloud.google.com/auth/clients/create
- App Type: **Web application**
- Add redirect URI: `http://localhost:8080/`
- Click **Create** and then download the credentials file
- Rename the file to `credentials.json`
- Place it in your project’s **root directory**

### 4. Enable Google Drive API
- Go to: https://console.cloud.google.com/marketplace/product/google/drive.googleapis.com
- Click **Enable**

### 5. Add Policy Documents to Drive
- In Google Drive, create a folder named: `BMVSI_HR_POLICIES`
- Upload all company **HR** policy documents to this folder

---

## 🧪 App Setup Instructions

### 1. Download or Clone the Project

If downloaded as a ZIP, extract it. Or use Git:

```bash
git clone https://github.com/bmv/intellectops/agno-agents.git
cd agno-agents
```

---

### 2. Create and Activate Python Virtual Environment

#### Windows:
```bash
python -m venv venv
venv\Scripts activate
```

#### macOS/Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 3. Install Required Python Packages

```bash
pip install -r requirements.txt
```

---

### 4. Add Your Environment Variables

Create a `.env` file in the root folder of the project:

```env
GEMINI_API_KEY='your-api-key-here'
NOTIFIER_EMAIL='your-email-for-sending-mail-to-HR'
NOTIFIER_EMAIL_PASSWORD='your-email-password (app-password not original one)'
HR_EMAIL='hr-email'
```

You can generate this Gemini API key from: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)

---

### 5. Place the OAuth Credentials

Ensure the `credentials.json` file downloaded earlier is placed in the **root** of your project directory.

---

### 6. Start the Application Server

Run the following command:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

---

## 🌐 Access the Application

Visit [http://localhost:8000](http://localhost:8000) in your browser to interact with the FastAPI-powered HR AI chatbot.

---

## ❗ Important Notes

- ✅ `.env` file is required and must include `GEMINI_API_KEY`
- ✅ `credentials.json` must be placed in the **root folder**
- 🔒 Ensure the `BMVSI_HR_POLICIES` Drive folder is accessible by the app (share with service account if needed)

---

## 🆘 Troubleshooting

- Check that your `.env` and `credentials.json` files are present and correctly configured
- Make sure your Google Drive folder is named exactly: `BMVSI_HR_POLICIES`
- Confirm your Google Cloud OAuth app is set up properly
- For further help, contact the development or IT team

---
