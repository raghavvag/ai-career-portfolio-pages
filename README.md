# 🤖 AI Career Agent – WhatsApp Portfolio Generator

AI Career Agent is a WhatsApp-based AI bot that helps users create a professional online portfolio and a downloadable PDF resume just by chatting.  
No website builders, no coding, no payments – just send messages on WhatsApp and get your portfolio deployed automatically.

---

## 🚀 What This Project Does

A user can:

1. Say **"Hi"** on WhatsApp  
2. Chat with the bot to provide:
   - Name
   - Role
   - Skills
   - (Later: GitHub, LinkedIn PDF, Resume upload)
3. The system:
   - Generates a clean HTML portfolio
   - Generates a PDF version using Puppeteer
   - Publishes both to **GitHub Pages**
4. The user receives:
   - A live website link
   - A downloadable PDF link

Example output:

🌐 Website: https://raghavvag.github.io/ai-career-portfolio-pages/users/whatsapp_916395286277-xxxx/index.html
📄 PDF: https://raghavvag.github.io/ai-career-portfolio-pages/users/whatsapp_916395286277-xxxx/portfolio.pdf

yaml
Copy code

---

## 🧠 Architecture Overview

User (WhatsApp)
|
v
Twilio WhatsApp Webhook
|
v
Node.js Backend (Express)
|
+-- Firestore (User state + profile draft)
+-- Puppeteer (PDF generation)
+-- HTML Generator
+-- GitHub API (Deploy files)
|
v
GitHub Pages (Public portfolio hosting)

yaml
Copy code

---

## 📁 Project Structure

src/
├── config/
│ └── firebase.ts
├── controllers/
│ └── webhook.controller.ts
├── services/
│ ├── convo.service.ts
│ ├── conversationManager.ts
│ ├── githubService.ts
│ ├── portfolioService.ts
│ ├── pagePublisher.ts
│ └── twilio.service.ts
├── states/
│ └── convo.manager.ts
├── types/
│ └── states.types.ts
├── utils/
│ ├── htmlGenerator.ts
│ └── pdfGenerator.ts
├── index.ts
├── .env
├── package.json
└── tsconfig.json

yaml
Copy code

---

## ⚙️ Tech Stack

| Layer        | Tech Used |
|-------------|----------|
| Chat Interface | Twilio WhatsApp API |
| Backend | Node.js + Express + TypeScript |
| Database | Firebase Firestore |
| PDF Generator | Puppeteer |
| Hosting | GitHub Pages |
| Deployment | GitHub REST API |
| State Management | Firestore (FSM based) |

---

## 🔐 Environment Variables

Create a `.env` file:

```env
PORT=8080

# Twilio
TWILIO_ACCOUNT_SID=your_sid
TWILIO_AUTH_TOKEN=your_token
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886

# Firebase
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"

# GitHub
GITHUB_USERNAME=raghavvag
GITHUB_REPO=ai-career-portfolio-pages
GITHUB_TOKEN=your_github_pat
GITHUB_PAGES_BASE=https://raghavvag.github.io/ai-career-portfolio-pages
🧪 Current Conversation Flow
User sends Hi

Bot asks name

Bot asks role

Bot asks skills

Portfolio is generated automatically

HTML + PDF deployed

Links sent back to WhatsApp

State machine:

powershell
Copy code
start → await_name → await_role → await_skills → generate → completed
🛠 Deployment Repo Structure (GitHub Pages)
The pages repo must look like:

pgsql
Copy code
ai-career-portfolio-pages/
└── docs/
    ├── index.html
    └── users/
        └── whatsapp_916395286277-uuid/
            ├── index.html
            └── portfolio.pdf
GitHub Pages source must be:

makefile
Copy code
Branch: main  
Folder: /docs
🧩 Why This Design is Powerful
Zero cost hosting (GitHub Pages)

No UI required (WhatsApp only)

Scalable

Feature expandable:

GitHub project import

LinkedIn PDF parsing

Resume upload

spaCy NLP extraction

HuggingFace bio generation

Job matching & JD scoring

🏁 Current Status
✔ WhatsApp → Backend working
✔ Conversation FSM implemented
✔ HTML portfolio generator
✔ PDF resume generator
✔ GitHub Pages deployment
✔ Public URLs returned to user

🔮 Next Features (Planned)
GitHub username → auto project import

LinkedIn PDF upload

Resume PDF parsing

spaCy microservice for data extraction

Job description matching

ATS score + recommendations

Voice note support

🧠 Vision
“Your professional AI career agent, created in minutes, just by chatting.”

This project removes the technical and financial barrier to creating professional portfolios and resumes, starting directly from WhatsApp.

Built by Raghav Agrawal 🚀
