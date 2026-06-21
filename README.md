✍️ WhatsApp AI Agent

An AI-powered WhatsApp automation agent built with **n8n** that automatically 
receives incoming messages and generates intelligent, context-aware replies 
using an LLM — enabling fully automated WhatsApp conversations.

---

## 🚀 Features

- 💬 **Auto-receives** incoming WhatsApp messages
- 🧠 **AI understands** message context and intent
- ✍️ **Generates human-like replies** tailored to each message
- 📤 **Auto-sends responses** instantly
- ⚡ **Real-time processing** — replies within seconds
- 🔄 **Fully automated** — no manual responses needed

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation engine |
| Anthropic Claude / Gemini | AI message understanding & reply generation |
| WhatsApp Cloud API (Meta) | Message receiving and sending |

---

## 🔄 How It Works
WhatsApp Message Received

↓

Webhook Trigger Fires in n8n

↓

Message Content Extracted

↓

Sent to AI Model (Claude / Gemini)

↓

AI Generates Contextual Reply

↓

Reply Sent Back via WhatsApp

---

## ⚙️ Setup & Installation

1. Make sure you have **n8n** running (local or cloud)
2. Import the `whatsapp-ai-agent.json` file into your n8n instance
3. Add your **LLM API key** (Anthropic or Gemini) in credentials
4. Set up **WhatsApp Cloud API** via Meta Developer Console
5. Connect your **webhook URL** to the WhatsApp Cloud API
6. **Activate** the workflow
7. Done — your WhatsApp now replies automatically!

---

## 📁 Project Structure
whatsapp-ai-agent/

│

├── whatsapp-ai-agent.json   # n8n workflow file (import this)

└── README.md                # Project documentation

---

## 🧠 AI Integration

The AI layer handles the full conversation logic:
- **Understands the intent** behind each WhatsApp message
- **Generates natural, human-like replies** that feel conversational
- **Adapts tone** based on the message context
- **Handles varied inputs** — questions, requests, greetings, complaints
- Works with both **Anthropic Claude** and **Google Gemini** interchangeably

---

## ⚡ Challenges & How I Solved Them

### 1. 🔑 API Credit Exhaustion Mid-Development
**Problem:** The Anthropic API key ran out of credits during active testing, 
completely blocking the AI response generation step.  
**Solution:** Switched to Google Gemini (free tier via Google AI Studio) as a 
drop-in replacement. This also reinforced designing the AI node to be 
**provider-agnostic** — making it easy to swap between Claude and Gemini 
without rebuilding the workflow from scratch.

### 2. ⚙️ Incorrect Trigger Configuration
**Problem:** The "Source for Prompt" setting inside n8n was incorrectly set to 
"Define below" instead of reading from the connected trigger node — meaning the 
AI was receiving empty input and generating irrelevant replies.  
**Solution:** Corrected the setting to **"Connected Chat Trigger Node"** so the 
AI properly receives the incoming WhatsApp message before generating a response. 
A small config fix that made the entire workflow function correctly.

### 3. 🌐 Webhook Accessibility for WhatsApp
**Problem:** WhatsApp Cloud API requires a **publicly accessible HTTPS webhook URL** 
to deliver messages — but running n8n locally on a laptop means there is no 
public URL available by default.  
**Solution:** For development and portfolio purposes, the agent works as a 
chat-based trigger locally. For a full production deployment, the solution is 
to either host n8n on a cloud VPS or use a Cloudflare Tunnel to expose the 
local webhook securely to the internet — a pattern I have already implemented 
in other projects.

### 4. ⚠️ Rate Limiting on Free Tier
**Problem:** During back-to-back message testing, Gemini's free-tier rate limits 
were hit, causing the agent to fail silently on rapid incoming messages.  
**Solution:** Documented the limitation clearly and designed the workflow with 
throttling in mind. For production use, a paid API tier or a message queue 
would handle high message volumes reliably.

---

## 💡 Use Cases

- Customer support automation
- Business inquiry handling
- E-commerce order confirmations
- Appointment booking automation
- FAQ auto-responses

---

## 📌 Note on WhatsApp Connection

This workflow is designed to connect with the **WhatsApp Cloud API (Meta)**. 
For portfolio demonstration purposes it runs as a chat-based agent locally. 
Full WhatsApp integration requires a Meta Developer account and an approved 
WhatsApp Business number.

---

## 🙋‍♂️ Author

**Asad** — Software Engineer  
Building AI-powered automation tools for real-world use cases.# whatsapp-ai-agent
AI-powered WhatsApp agent built with n8n that automatically responds to WhatsApp messages using an LLM
