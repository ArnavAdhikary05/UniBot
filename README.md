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
2️⃣ Environment Variables
Create a .env file:

ini
Copy code
GEMINI_API_KEY=your_google_gemini_api_key_here
3️⃣ Run the Flask API
bash
Copy code
python api_server.py
API endpoint: http://localhost:5000/chat

Testing the API
Using Python:
python
Copy code
import requests

r = requests.post("http://localhost:5000/chat", json={
    "message": "Hello",
    "session_id": "test1"
})
print(r.json())
Using PowerShell:
powershell
Copy code
Invoke-RestMethod -Uri "http://localhost:5000/chat" -Method Post -ContentType "application/json" -Body '{"message":"hello","session_id":"test1"}'
WhatsApp Integration (Local Testing)
Install Node.js and dependencies:

bash
Copy code
npm install whatsapp-web.js qrcode-terminal axios
Run the client:

bash
Copy code
node whatsapp_client.js
Scan the QR code using WhatsApp mobile app.
Messages sent will be forwarded to your chatbot API, and responses will be sent back.

Telegram Integration
Create a bot using BotFather and get BOT_TOKEN.

Update TOKEN in telegram_bot.py.

Run the bot:

bash
Copy code
python telegram_bot.py
Messages sent to the bot will be forwarded to the Flask API and replied back.

Knowledge Base
Store official university information in knowledge/universitydata.txt.

The chatbot retrieves relevant information using sentence embeddings and FAISS.

Session Logging
Chat sessions are stored in chatlogs/ as JSON files:

json
Copy code
[
  {
    "time": "2025-09-14T12:10:30+00:00",
    "user": "hello",
    "bot": "Hello! How can I assist you today?"
  }
]
Each session is tracked separately using session_id.

Website Integration
Call the same Flask API from any website:

javascript
Copy code
fetch("http://yourserver.com/chat", {
  method: "POST",
  headers: {"Content-Type": "application/json"},
  body: JSON.stringify({message: "hi", session_id: "webuser1"})
})
.then(res => res.json())
.then(data => console.log(data.reply));
Deployment
For production, deploy Flask API using Gunicorn + Nginx, Render, Railway, or Google Cloud Run.

Update WhatsApp/Telegram clients with the public URL of the API.

Requirements
nginx
Copy code
flask
python-dotenv
google-generativeai
sentence-transformers
faiss-cpu
requests
python-telegram-bot
License
MIT License (free to use and modify)

yaml
Copy code

---

If you want, I can also make a **shorter, GitHub “repository description” version** that fits in the top of your repo page perfectly.  

Do you want me to do that?
