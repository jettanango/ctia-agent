# 🛡️ CTIA — Cyber Threat Intelligence Agent

<p align="center">
  <img src="https://img.shields.io/badge/Google%20Gemini-API-blue?logo=google&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3.10+-yellow?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Platform-Google%20Colab-orange?logo=googlecolab&logoColor=white" />
  <img src="https://img.shields.io/badge/Alert-Google%20Chat-green?logo=googlechat&logoColor=white" />
  <img src="https://img.shields.io/badge/Kaggle-Capstone%20Project-teal?logo=kaggle&logoColor=white" />
</p>

> **Capstone Project** — Google x Kaggle 5-Day AI Agents Intensive Course (June 2026)  
> Track: Freestyle | Language: Python | Runtime: Google Colab

---

## 📌 ภาพรวมโปรเจกต์

**CTIA (Cyber Threat Intelligence Agent)** คือ AI Agent ที่พัฒนาด้วย **Google Gemini API** เพื่อทำหน้าที่ติดตาม วิเคราะห์ และแจ้งเตือนภัยคุกคามไซเบอร์แบบอัตโนมัติ

ระบบจะดึงข่าวช่องโหว่ล่าสุดจาก **CISA (Cybersecurity and Infrastructure Security Agency)** นำมาวิเคราะห์ แปลเป็นภาษาไทย และสรุปสำหรับผู้บริหาร จากนั้นส่งแจ้งเตือนเข้า **Google Chat** โดยอัตโนมัติ

---

## 🎯 ปัญหาที่แก้ไข

องค์กรส่วนใหญ่ขาดทรัพยากรในการติดตามข่าวภัยคุกคามไซเบอร์แบบ Real-time โดยเฉพาะในรูปแบบภาษาไทยที่เข้าใจง่ายสำหรับผู้บริหาร CTIA แก้ปัญหานี้ด้วยการทำให้กระบวนการทั้งหมดเป็นอัตโนมัติภายใน Pipeline เดียว

---

## 🏗️ สถาปัตยกรรมระบบ

```
┌─────────────────────────────────────────────────────┐
│                   CTIA Agent                        │
│                                                     │
│  ┌──────────┐   ┌──────────────┐   ┌─────────────┐ │
│  │  Tool 1  │──▶│    Tool 2    │──▶│   Tool 3    │ │
│  │ ดึงข่าว  │   │วิเคราะห์+แปล│   │ ส่งแจ้งเตือน│ │
│  │  RSS     │   │  (Gemini)   │   │(Google Chat)│ │
│  └──────────┘   └──────────────┘   └─────────────┘ │
│       │                │                  │         │
│    CISA API        Gemini API        Webhook API    │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Python Tools ทั้ง 3 ตัว

| # | ฟังก์ชัน | หน้าที่ | Input | Output |
|---|---------|---------|-------|--------|
| 1 | `fetch_threat_news()` | ดึงข่าวช่องโหว่จาก CISA RSS Feed | `source: str` | ข้อความข่าวดิบ |
| 2 | `analyze_and_summarize()` | ให้ Gemini แปล+สรุปเป็นภาษาไทย | `raw_news: str` | รายงานภาษาไทย |
| 3 | `send_to_google_chat()` | ส่งรายงานเข้า Google Chat | `message: str` | `status 200` |

---

## ✨ ฟีเจอร์หลัก

- 🔍 **ดึงข่าวอัตโนมัติ** จาก CISA Cybersecurity Advisories
- 🌏 **แปลและสรุปภาษาไทย** ด้วย Google Gemini
- 📊 **วิเคราะห์ระดับความเสี่ยง** สูง / กลาง / ต่ำ
- 📨 **แจ้งเตือน Real-time** ผ่าน Google Chat Webhook
- 🧹 **ทำความสะอาด HTML** อัตโนมัติก่อนส่งให้ Gemini

---

## 🚀 วิธีติดตั้งและใช้งาน

### 1. เตรียม Environment

```bash
pip install google-genai requests
```

### 2. ตั้งค่า Environment Variables

คัดลอกไฟล์ `.env.example` แล้วเปลี่ยนชื่อเป็น `.env`:

```bash
cp .env.example .env
```

แก้ไขค่าในไฟล์ `.env`:

```env
GOOGLE_API_KEY=your_gemini_api_key_here
GOOGLE_CHAT_WEBHOOK=your_google_chat_webhook_url_here
```

### 3. รันบน Google Colab

เปิดไฟล์ `ctia_agent.ipynb` บน Google Colab แล้วรัน Cell ตามลำดับ:

| Cell | หน้าที่ |
|------|---------|
| Cell 1 | ติดตั้ง Library |
| Cell 2 | ตั้งค่า API Key |
| Cell 3 | ทดสอบ Gemini |
| Cell 4 | Tool 1: ดึงข่าว |
| Cell 5 | Tool 2: วิเคราะห์ |
| Cell 6 | Tool 3: ส่ง Google Chat |
| Cell 7 | รัน Agent เต็มรูปแบบ |

---

## 📁 โครงสร้างไฟล์

```
ctia-agent/
├── ctia_agent.ipynb      # โค้ดหลักทั้งหมด (Google Colab Notebook)
├── README.md             # เอกสารโปรเจกต์ (ไฟล์นี้)
├── .env.example          # ตัวอย่าง Environment Variables
└── .gitignore            # ป้องกัน .env จริงขึ้น GitHub
```

---

## 🔐 ความปลอดภัย

> ⚠️ **สำคัญ:** ห้ามอัปโหลด API Key จริงขึ้น GitHub เด็ดขาด  
> ใช้ไฟล์ `.env` สำหรับเก็บข้อมูลลับ และเพิ่ม `.env` ใน `.gitignore` เสมอ

---

## 🔧 Tech Stack

| เทคโนโลยี | การใช้งาน |
|-----------|----------|
| Python 3.10+ | ภาษาหลัก |
| Google Gemini API (`gemini-2.0-flash`) | AI วิเคราะห์และแปลภาษา |
| Google Colab | Runtime Environment |
| CISA RSS Feed | แหล่งข้อมูลข่าวภัยคุกคาม |
| Google Chat Webhook | ช่องทางแจ้งเตือน |
| `requests` + `xml.etree.ElementTree` | ดึงและ Parse XML |
| `re` (regex) | ทำความสะอาด HTML |

---

## 📈 ผลลัพธ์ตัวอย่าง

ระบบวิเคราะห์ช่องโหว่จาก CISA แล้วสรุปเป็นภาษาไทย เช่น:

```
🛡️ CTIA Daily Alert

ตรวจพบช่องโหว่ความปลอดภัยระดับวิกฤตใน 3 กลุ่มเทคโนโลยี:
ระบบควบคุมดาวเทียม, อุปกรณ์ IoT และสถานีรับส่งสัญญาณดาวเทียม

ระดับความเสี่ยง: 🔴 สูง (High)
แนะนำ: เร่งอัปเดต Firmware Patch ทันที
```

---

## 👤 เกี่ยวกับผู้พัฒนา

พัฒนาเป็นส่วนหนึ่งของ **Google x Kaggle 5-Day AI Agents Intensive Course**  
Capstone Project Track: Freestyle

---

## 📄 License

MIT License — ใช้งานได้อย่างอิสระ
