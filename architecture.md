# 🧠 Local AI Architecture Notes

## 📌 Overview
This document outlines the architecture for my **local AI system** using **LLaMA 3**, including:
- **Model hosting**
- **Persistent memory**
- **Storage solutions**
- **APIs & interaction**
- **Hardware considerations**
- **Smart home integration**
- **Automation learning & refinement**
- **Future expansion plans**

---

## **1️⃣ AI Model - LLaMA 3**
### **What is a Model?**
- A **model** is a trained function that **predicts the next token** in a sequence.
- It **doesn't inherently have a UI or chat interface**—it just generates responses based on input.

### **How Do I Interact With It?**
- **Command Line (Basic Testing)**
- **API Server (Best for Automation & UI)**
- **Custom UI (Building a Chat Interface)**

### **Best Tools for Running LLaMA 3 Locally**
| Tool                         | Features                                      | OpenAI API Compatible? |
|------------------------------|-----------------------------------------------|------------------------|
| **Ollama**                   | Easiest setup, optimized model loading       | ✅ Yes                 |
| **Text-Generation-WebUI**     | Advanced UI, supports chat history & tuning  | ✅ Yes                 |
| **Llama.cpp**                 | Lightweight, CPU-optimized                   | ❌ No (but can be adapted) |

---

## **2️⃣ Persistent Memory**
### **Why Local AI Doesn’t Have Memory by Default**
- **Models do not retain memory**—each response is independent.
- **Memory has to be stored externally** and reloaded into context when needed.

### **Types of Memory Storage**
| Type                      | Usage Scenario                               | Pros | Cons |
|---------------------------|----------------------------------------------|------|------|
| **Short-Term (Context Window)** | Holds session memory in RAM | Fast | Loses data when restarted |
| **SQL Database (Structured Memory)** | Stores chat history and user data | Easy retrieval, structured | Not great for meaning-based recall |
| **Vector Database (Semantic Memory)** | Stores embeddings for deep AI recall | Intelligent memory retrieval | Requires more storage and compute |

### **Hybrid Memory Approach (Best Choice)**
✅ **Short-term memory** (RAM) → Keeps recent chat history.  
✅ **SQL database** → Stores structured interactions for lookup.  
✅ **Vector database (FAISS/ChromaDB)** → Enables long-term AI knowledge retrieval.  

---

## **3️⃣ API & Interaction**
### **How to Talk to My Local AI**
- **Run the model as an API server** → Interact using HTTP requests.
- **Most local AI models support OpenAI’s API format**, meaning I can integrate them into automation workflows.

### **Node-RED Integration**
- **Node-RED can interact with local AI** by sending HTTP requests.
- Example:
  - **Trigger:** Sensor input, voice command, or button press.
  - **Action:** AI processes the request and sends back a response.

### **🖥️ Custom Chat Interface for Local AI**
- **Goal:** Build a ChatGPT-like UI for seamless interaction with the local AI model.  
- **Why?** The ChatGPT interface is intuitive, but using a local model allows for **full control** without API limits or moderation.  
- **Approach:**  
  ✅ **Frontend:** Web-based UI built with **Flask + HTML/CSS/JS** for a familiar chat experience.  
  ✅ **Backend:** Connects to **local Llama 3 API** using OpenAI-compatible API requests.  
  ✅ **Features:**  
    - **Persistent chat history** stored in an SQL database.  
    - **Markdown support** for clean formatting.  
    - **Customizable themes & UI tweaks.**  
    - **Optional voice input/output integration.**  
- **Long-Term Plan:** Eventually replace ChatGPT usage entirely with a **fully self-hosted AI assistant.**  

---

## **4️⃣ Storage Considerations**
### **Why NVMe is Needed**
- **AI models and databases require high-speed storage**.
- **NVMe SSDs are ideal** for:
  - Fast database queries (SQL & vector DBs).
  - Quick AI model response times.
  - Reducing read/write bottlenecks.

### **Recommended Storage Setup**
| Component        | Storage Type  | Size Recommendation |
|-----------------|--------------|--------------------|
| **OS + AI Model** | NVMe SSD | **1-2TB** |
| **Memory Storage (SQL + Vector DB)** | NVMe SSD or Large SSD | **4TB+** |
| **Archived Logs / Extra Data** | HDD (Optional) | **Depends on need** |

---

## **📦 Rack & Power Planning**
- **User is setting up a permanent rack mount system.**
- **Plan:** 4U enclosure for AI server, rack-mountable UPS, and PoE switch.
- **Estimated Cost:** **$1,238 - $1,538**.
- **Placement:** **Likely in bedroom closet with ventilation.**
- **Considerations:**
  ✅ Needs a **window** for A/C cooling.  
  ✅ **Noise levels acceptable** (user likes white noise).  
  ✅ **Permanent placement** (no seasonal moves required).  
  ✅ **Ubiquiti PoE Switch** for network integration.  

### **PoE Switch Considerations**
- **User prefers Ubiquiti networking hardware** and plans to **keep infrastructure entirely Ubiquiti.**  
- **Rack-mountable PoE switch planned** for clean integration with the server setup.  
- **PoE cable runs should stay under 100m, so no special extenders are needed.**  

### **Power & Backup**
- **UPS required for AI server** (network UPS already in place).  
- **Rack-mountable UPS planned** for power protection & clean setup.  
- **Placement must allow for proper cooling & ventilation.**  

---

## **5️⃣ Home Assistant Configuration Management**
✅ **AI managing HA configuration is planned for future implementation.**  
✅ **Home Assistant is moving away from YAML, which may affect AI control methods.**  
✅ **User will investigate the `.config` directory inside HA to determine how configuration is stored.**  
✅ **If YAML remains, AI can modify files directly; if HA shifts to UI-based settings, AI will need API-driven configuration changes.**  

---

## **6️⃣ AI-Driven Automation Learning & Refinement**
✅ **AI detects patterns via InfluxDB logs and suggests automation rules.**  
✅ **AI only modifies automations it originally created unless explicitly told otherwise.**  
✅ **AI confirms major behavior shifts before adjusting automations.**  
✅ **Rejected automations (and reasons) are stored to refine future suggestions.**  

---

## **7️⃣ Backup & Redundancy Considerations**
✅ **AI server hardware planning is delayed for later.**  
✅ **Need to determine if AI requires a backup/failover server.**  
✅ **Automated backup strategy (Tarsnap, NAS, cloud storage options) needs planning.**  
✅ **Retention policy for automation history & long-term AI learning data to be decided.**  

---

## **8️⃣ Multi-Room AI Audio & Dynamic Volume Adjustment**
✅ **Speakers are shared for AI & music (Home Assistant manages control).**  
✅ **Dynamic volume adjustment based on background noise (low/medium/high).**  
✅ **Volume resets to default after 5 minutes of inactivity.**  
✅ **Manual override for speaker selection & volume changes.**  

---

## **9️⃣ Finalized Microphone Setup**
| Room          | Microphone        | Price  | Notes |
|--------------|------------------|-------|-------|
| **Living Room** | **Rode NTG4+** | $299 | Shotgun mic for isolating voice in a noisy space |
| **Bedroom** | **Rode NT1 5th Gen** | $249 | Large-diaphragm condenser for warm, natural sound |
| **Kitchen** | **AT2020 (Existing)** | N/A | Moved from the bedroom |
| **Office** | **Blue Ember (XLR)** | N/A | Works well in a small, quiet space |
| **Guest Bedroom** | **Blue Yeti** | $97 | Cost-effective with full-room coverage |

✅ **More rooms may need microphone setups later, but this is a strong starting point.**  

---

## **🔮 Future Expansion – AI Intercom & Remote Control**
✅ **AI will eventually act as an intercom via phone, with a custom app planned later.**  
✅ **Will need to determine if remote voice commands require speaker recognition or manual activation.**  
✅ **AI should be able to handle intercom-style commands between rooms.**  

---

## **🔄 Future Planning (For Later Implementation)**
✅ **AI Server Hardware & Cost Estimation** – Planning delayed for later.  
✅ **Email Automation** – AI will draft & send emails via Node-RED when requested.  

---

📝 **Notes Last Updated:** *March 2, 2025*  