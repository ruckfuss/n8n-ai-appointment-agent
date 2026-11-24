24/7 AI Appointment Booking & Notification Agent (n8n)

A self-hosted AI Agent workflow built with n8n, Docker, LLM APIs (OpenAI / Groq / Gemini), and Telegram that automates customer inquiries, captures appointment details across multi-turn conversations, and dispatches real-time booking alerts.

Key Features

Multi-Turn Conversational Memory: Uses Simple Memory (Window Buffer) so the assistant remembers customer names, requested services, phone numbers, and preferred times across messages.

Autonomous Tool Calling: Automatically extracts structured booking details from free-form chat and triggers the Telegram Tool to send instant notifications to business owners.

Zero-Cost Self-Hosting: Runs locally or on any VPS via Docker with persistent volume storage (~/.n8n).

Website Embed Ready: Exposes a public chat widget endpoint via n8n's Chat Trigger node for quick integration into any website.

Architecture

Customer Message (Chat Trigger)
        │
        ▼
   [ AI Agent ] ◄──── LLM Chat Model (Groq / OpenAI / Gemini)
        │       ◄──── Simple Memory (Conversation Context)
        ▼
  Telegram Tool ────► Instant Booking Alert to Business Owner


Quick Start (Docker)

Start a persistent local n8n instance:

docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n --restart unless-stopped n8nio/n8n


Open http://localhost:5678, create a new workflow, and select Import from file to load workflow.json.

Add your own LLM API Key and Telegram Bot Token inside n8n's Credentials panel (no secrets are stored in this repository).

Customize the System Message inside the AI Agent node with your business services, pricing, and hours.

Tech Stack

Workflow Engine: n8n (Self-Hosted via Docker)

AI / LLM: LangChain AI Agent Node (Groq / OpenAI / Google Gemini)

Notifications: Telegram Bot API
