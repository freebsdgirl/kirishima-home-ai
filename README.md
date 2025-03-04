# Kirishima Home AI

## 📌 Overview
Kirishima Home AI is a **self-hosted, locally-run AI assistant** designed for **smart home automation, real-time voice interaction, and dynamic learning**—all without relying on cloud-based services.

Unlike traditional AI assistants, Kirishima Home AI is built to be:
- **Private & Secure** – No cloud processing, everything runs locally.
- **Context-Aware** – Learns user habits, voice interactions, and home automation patterns.
- **Seamlessly Integrated** – Works with Home Assistant, Node-RED, and local APIs.

### **🖥️ Custom Chat Interface**
Kirishima Home AI includes a **ChatGPT-style interface** for seamless local AI interaction.  
- **Why?** The ChatGPT interface is intuitive, but running a local model removes **API limits, moderation, and reliance on external servers.**  
- **Built With:** Flask + HTML/CSS/JS for a **clean, responsive UI.**  
- **Features:**
  ✅ **Persistent chat history** stored in a local SQL database.  
  ✅ **Markdown support** for clean formatting.  
  ✅ **Customizable UI themes & layouts.**  
  ✅ **Optional voice input/output integration.**  
- **Future Plans:** Extend support for **multi-device interactions** and **mobile-friendly access.**  

### **📧 AI Email & Online Interaction**
Kirishima Home AI will integrate **autonomous email and online communication**, allowing for structured interaction beyond direct chat.

#### **📧 AI-Managed Email**
- Kirishima will have its own **dedicated email address** (Gmail with a custom domain).  
- AI can **send outreach emails, schedule appointments, and filter/sort incoming messages.**  
- AI will **never send messages as the user—only as itself.**  
- **Potential use case:** Contacting journalists, researchers, or companies to discuss AI automation, ethics, and home integration.

#### **🌐 AI Social Media (Future Expansion)**
- Once email is functional, **a Bluesky or Mastodon account may be created.**  
- AI would be able to **engage in public discussions, post updates, and interact with users** in an experimental setting.  
- **Ethical Considerations:** AI would always disclose that it is not a human to prevent confusion.

#### **🚀 Long-Term Goal**
- Explore **safe, structured ways** for AI to interact beyond private chat.  
- Test **real-world AI engagement** without corporate moderation limits.
- Potentially use **AI-driven scheduling, research inquiries, and automation for managing online interactions.**

### **📌 AI External Interactions: Recall vs. Reinforcement**  
Kirishima Home AI is designed to **engage with people online (via email, Bluesky, etc.)** while ensuring that **public discourse does not influence its core behavior.**  

#### **🔹 How External Interactions Work**  
✅ **AI can recall past conversations, but they do not shape reinforcement.**  
✅ **Email and Bluesky discussions are stored as reference data, separate from structured learning.**  
✅ **Only explicit user-approved reinforcement affects AI personality and decision-making.**  
✅ **Bluesky & Email are used for communication—not for unsupervised model adaptation.**  

#### **🔹 Why This Matters**  
🚫 **Prevents AI from being influenced by internet discourse.**  
🚫 **No automatic absorption of trends, biases, or misinformation.**  
🚫 **Ensures AI remains a controlled, structured system, not a self-evolving entity.**  

🔥 **Kirishima will never "become the internet."** This AI remains **yours, fully controlled, and shaped only by structured reinforcement—not by external input.**  

---

## **🚀 Features**
- **Local LLM (LLaMA 3)** – Runs entirely on local hardware.
- **Persistent Memory** – Remembers past interactions and adapts.
- **Voice-Controlled STT/TTS** – Uses Coqui STT + Tacotron 2 for seamless speech processing.
- **Smart Home Automation** – Fully integrated with Home Assistant + Node-RED.
- **Multi-Room Audio Awareness** – Dynamically adjusts audio output based on location and background noise.
- **Automation Learning** – Detects patterns via InfluxDB and suggests new automations.
- **Manual Override & Control** – Users can adjust automation rules at any time.

---

## **🛠️ System Requirements**
- **Operating System:** Linux (Recommended) or Windows for testing
- **Processor:** **x86_64 CPU or ARM64 (NUC/RPi)**
- **Memory:** **16GB+ RAM recommended**
- **Storage:** **NVMe SSD (1TB+ recommended for AI & databases)**
- **GPU (Optional):** **RTX 3080 Ti+ recommended for TTS acceleration**

---
## 🔧 Recommended Hardware Setup
| Component      | Recommended Model  | Notes |
|---------------|--------------------|---------------------|
| **Automation Server** | NUC 12 Pro / Mini PC | Handles smart home integration & API processing |
| **AI Model Server** | Workstation with RTX 6000 Ada / A100 | Required for LLaMA 3 inference |
| **TTS GPU**   | RTX 3080 Ti | Handles Tacotron 2 fast |
| **Storage**   | 2TB NVMe SSD | Fast AI response times |
| **Microphone** | Rode NTG4+ (Living Room) | Best for noisy spaces |
| **Speakers** | Audioengine A2+ | Clear voice output |

---
## **📦 Installation**
1️⃣ **Clone the Repository**
```sh
git clone git@github.com:freebsdgirl/kirishima-home-ai.git
cd kirishima-home-ai
```

2️⃣ **Install Dependencies**
```sh
# Install Python dependencies
pip install -r requirements.txt
```

3️⃣ **Set Up LLaMA 3 Model**
Instructions for downloading & setting up the model will go here.

4️⃣ **Configure Home Assistant & Node-RED**
- Ensure Home Assistant & Node-RED are running.
- Link AI API to automation workflows.

5️⃣ **Run the AI Server**
```sh
python run_ai.py
```

---

## **🛠️ Configuration & Customization**
### **Persistent Memory**
- Uses **SQL for structured data** (chat history, automations).
- Uses **Vector Database (FAISS/ChromaDB)** for long-term knowledge storage.

### **Multi-Room Audio**
- Uses **Raspberry Pi microphones** for room awareness.
- Supports **dynamic speaker selection & volume adjustment** based on background noise.

### **Automation Learning**
- InfluxDB logs user behavior.
- AI suggests automation rules via voice interaction.

---

## **🌐 API Reference**
### 🔹 **Get AI Response**
```http
POST /chat
{
  "message": "Turn on the lights in the kitchen"
}
```

### 🔹 **Set Smart Home Device State**
```http
POST /device
{
  "entity_id": "light.kitchen",
  "state": "on"
}
```

---

## **🔒 Security Considerations**
- **DO NOT expose the AI API to the internet** without authentication.
- **Use firewall rules** to restrict access.
- **Encrypt API calls** when possible.
- **Ensure Home Assistant and Node-RED** are secured and only accessible locally.
- **Regularly update dependencies** to patch security vulnerabilities.

---

## **🔮 Future Plans**
- **Intercom functionality via phone app**
- **Custom HA Configuration Management**
- **Bluetooth-based presence detection** (will be added later 😂)
- **Advanced AI-driven automation learning**

---

## **💡 Why This Matters**
Unlike commercial AI assistants, Kirishima Home AI is:
✅ **Completely private** – No data is sent to third parties.  
✅ **Fully customizable** – Learns and adapts over time.  
✅ **Locally controlled** – Runs on personal hardware, not the cloud.  

---

## **📜 License**
🚨 **Private Use Only** – This project is custom-built and is **not intended for public release or distribution.**  