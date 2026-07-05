# ctia-agent
CTIA-Agent — Cyber Threat Intelligence Agent An agent that fetches cyber threat news from CISA, analyzes it using Gemini, and sends alerts to Google Chat.

# 🛡️ CTIA — Cyber Threat Intelligence Agent

Agent สำหรับดึงข่าวภัยคุกคามไซเบอร์จาก CISA 
วิเคราะห์ด้วย Gemini และส่งแจ้งเตือนเข้า Google Chat

## Tools
- Tool 1: fetch_threat_news() — ดึงข่าว RSS
- Tool 2: analyze_and_summarize() — วิเคราะห์ด้วย Gemini  
- Tool 3: send_to_google_chat() — ส่ง Webhook

## วิธีใช้
1. ใส่ API Key ใน .env
2. รัน ctia_agent.ipynb ใน Google Colab
