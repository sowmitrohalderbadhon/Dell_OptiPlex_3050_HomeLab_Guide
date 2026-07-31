# Dell_OptiPlex_3050_HomeLab_Guide

# 🖥️ Dell OptiPlex 3050 Home Lab Server

A lightweight, power-efficient, self-hosted Home Lab server environment running **Ubuntu Server 24.04 LTS**. This setup utilizes **Docker Compose** to host local AI models via **Ollama & Open WebUI**, workflow automation with **n8n**, remote development via **code-server (VS Code Web)**, and local web hosting using **Nginx**.

---

## 📐 Hardware Specifications

* **Model:** Dell OptiPlex 3050 Micro
* **CPU:** Intel Core i5-7500T (4 Cores @ 2.70 GHz)
* **RAM:** 8GB DDR4 *(16GB Recommended for running 7B/8B LLMs)*
* **Storage:** 256GB NVMe SSD
* **Network:** Gigabit Ethernet (LAN) / Wi-Fi

---

## 🛠️ Stack & Architecture

* **OS:** Ubuntu Server 24.04 LTS
* **Containerization:** Docker & Docker Compose
* **Local AI Runtime:** Ollama (`llama3.2:3b` model)
* **Web Services:**
  * **Open WebUI:** User-friendly ChatGPT-style interface for local LLMs.
  * **n8n:** Self-hosted workflow and AI automation engine.
  * **code-server:** Full VS Code IDE running directly in the browser.
  * **Nginx:** Lightweight web server hosting local static applications/websites.

---

## 🚀 Getting Started

### 1. Prerequisites
* 8GB+ USB Flash Drive (Flashed with Ubuntu Server 24.04 LTS ISO using Rufus)
* Monitor & Keyboard (for initial setup only)
* Ethernet Cable for network stability

### 2. Initial OS Setup & SSH Access
1. Install **Ubuntu Server 24.04 LTS** on the entire SSD target.
2. Enable **OpenSSH Server** during OS installation.
3. Once booted, disconnect monitor/keyboard and access the server headlessly via SSH from your terminal:

```bash
ssh admin@<YOUR-SERVER-IP>
