# 🌍 Multilingual Chatbot with Knowledge Base, WhatsApp & Telegram Integration

## Project Overview
This project implements a multilingual campus chatbot using the **Google Gemini API**, capable of understanding English, Hindi, and other regional languages. It provides:

- **Knowledge base support:** Answers questions using official university data (`universitydata.txt`).
- **Session logging:** Stores all chat sessions in JSON files for later review.
- **REST API:** A Flask API that can be consumed by multiple clients.
- **WhatsApp & Telegram bots:** Forward user messages to the chatbot API and respond in real-time.

---

## Features
- Multilingual conversational AI
- Knowledge base retrieval (via embeddings + FAISS)
- Persistent JSON session logs
- REST API for integration with websites or mobile apps
- WhatsApp local testing client using `whatsapp-web.js`
- Telegram bot integration using `python-telegram-bot`

---

## Folder Structure
multilingual_chatbot_project/
│
├─ chatbot_core.py # Core chat logic + knowledge base
├─ api_server.py # Flask REST API
├─ whatsapp_client.js # WhatsApp integration
├─ telegram_bot.py # Telegram integration
├─ knowledge/
│ └─ universitydata.txt # Knowledge base
├─ chatlogs/ # JSON chat histories
├─ .env # Environment variables (GEMINI_API_KEY)
└─ requirements.txt

yaml
Copy code

---

## Setup Instructions

### 1️⃣ Python Environment
```bash
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # Linux/macOS
pip install -r requirements.txt
```

### 2️⃣ Environment Variables
Create a .env file:
```bash
GEMINI_API_KEY=your_google_gemini_api_key_here
```
### 3️⃣ Run the Flask API
```bash
Copy code
python api_server.py
API endpoint: http://localhost:5000/chat
```
