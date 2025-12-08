<div align="center">
  <h1>🦋 SL5 Auri (Lite)</h1>
  <p><strong>The lightweight, offline Voice Control for Embedded Systems & IoT.</strong></p>
  <p>Run powerful voice commands on < 500 MB RAM. No Cloud. No AI Hallucinations.</p>

  <a href="https://github.com/sl5net/SL5-aura-service">Based on SL5 Aura Core</a> • 
  <a href="#installation">Installation</a> • 
  <a href="#features">Features</a>
</div>

---

## 🧐 What is Auri?

**Auri** is the "little sister" of [SL5 Aura](https://github.com/sl5net/SL5-aura-service). While Aura is designed for high-end desktops with large AI models (Llama 3), **Auri is optimized for efficiency.**

It uses the same deterministic RegEx engine but strips away all heavy AI dependencies. This makes it perfect for:
*   🍓 **Raspberry Pi** (3, 4, 5, Zero 2W)
*   🤖 **Robotics & IoT Projects**
*   💻 **Older Laptops / Netbooks**
*   🔒 **Privacy Purists** (Strictly deterministic, no "fuzzy" AI logic)

| Feature | 🦁 **SL5 Aura** (Ultimate) | 🦋 **SL5 Auri** (Lite) |
| :--- | :--- | :--- |
| **Logic Engine** | RegEx + Llama 3.2 (LLM) | **RegEx Only** (100% Deterministic) |
| **RAM Requirement** | 4 GB - 8 GB | **< 500 MB** |
| **Speech Model** | Vosk Big (1.9 GB) | **Vosk Small** (45 MB) |
| **Install Size** | ~ 8 GB | **~ 300 MB** |

---

## 🚀 Installation

Auri uses a smart wrapper to install the SL5 Core in "Diet Mode".

### 1. One-Line Installer
```bash
# Clone this lightweight repo
git clone https://github.com/sl5net/auri.git
cd auri

# Run the installer wrapper
chmod +x install.sh
./install.sh
```

### 2. What happens now?
1.  The installer fetches the latest stable **SL5 Aura Core**.
2.  It installs system dependencies (Python, Vosk, Sound-Utils).
3.  It **EXCLUDES** all heavy AI tools (Ollama, Training Data, Large Models).
4.  It automatically downloads the **lightweight German model** (45 MB).

---

## 🎮 Usage

After installation, Auri behaves exactly like Aura, just faster and without the "Chat with AI" feature.

### Start the Service
```bash
# Start the background service
./scripts/start_aura_service.sh
```

### Add your own Commands
Edit the map files in `config/maps/`. Auri uses pure Python RegEx for matching.

```python
# config/maps/my_commands.py
from plugins import BaseMap

# Simple Rule: When you say "Light on", it runs the command
# Auri is deterministic: precise input = precise output.
my_map = [
    ("Licht an", r"(licht|lampe)\s+an", "kasa --plug 1 on"),
    ("System Status", r"status", "htop"),
]
```

---

## 🛠️ Hardware Recommendations

*   **CPU:** Any 64-bit CPU (ARM64 or x86_64). Single Core is enough.
*   **RAM:** 512 MB minimum (1 GB recommended for comfort).
*   **Microphone:** Any USB microphone or ReSpeaker HAT.

---

## ❤️ Credits

Auri is maintained by the [SL5NET](https://github.com/sl5net) team.
If you need the full power of LLMs (Ollama), check out the main project: **[SL5 Aura](https://github.com/sl5net/SL5-aura-service)**.

