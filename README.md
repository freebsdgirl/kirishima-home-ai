# Kirishima Home AI

## 📌 Overview
Kirishima Home AI is a **self-hosted, locally-run AI assistant** designed for **smart home automation, real-time voice interaction, and dynamic learning**—all without relying on cloud-based services.

Unlike traditional AI assistants, Kirishima Home AI is built to be:
- **Private & Secure** – No cloud processing, everything runs locally.
- **Context-Aware** – Learns user habits, voice interactions, and home automation patterns.
- **Seamlessly Integrated** – Works with Home Assistant, Node-RED, and local APIs.

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