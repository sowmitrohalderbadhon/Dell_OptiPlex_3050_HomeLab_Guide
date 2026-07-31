# 🖥️ Dell OptiPlex 3050 AI Home Lab Server

A complete self-hosted AI Automation Home Lab built on a **Dell OptiPlex 3050 Micro**, powered by **Ubuntu Server 24.04 LTS**, **Docker**, **Ollama**, **Open WebUI**, **n8n**, **VS Code Server**, and **Nginx**.

This project demonstrates how to transform an affordable mini PC into a lightweight AI server capable of running local LLMs, automation workflows, web development environments, and self-hosted services.

---

# 🚀 Features

* Ubuntu Server 24.04 LTS
* Docker & Docker Compose
* Ollama Local AI
* Llama 3.2 Lightweight Models
* Open WebUI (ChatGPT-style Interface)
* n8n Workflow Automation
* VS Code Server (Browser IDE)
* Nginx Local Web Server
* SSH Remote Management
* Lightweight & Energy Efficient
* Perfect for Learning, Development & AI Automation

---

# 🖥 Hardware

| Component | Specification               |
| --------- | --------------------------- |
| Machine   | Dell OptiPlex 3050 Micro    |
| CPU       | Intel Core i5-7500T         |
| RAM       | 8GB DDR4 (16GB Recommended) |
| Storage   | 256GB NVMe SSD              |
| Network   | Gigabit Ethernet / Wi-Fi    |

---

# 🛠 Technology Stack

* Ubuntu Server 24.04 LTS
* Docker
* Docker Compose
* Ollama
* Llama 3.2
* Open WebUI
* n8n
* VS Code Server
* Nginx
* OpenSSH

---

# 📂 Project Architecture

```text
                 Internet / Local Network
                          │
                          ▼
                 Ubuntu Server 24.04
                          │
        ┌──────────────────────────────────┐
        │             Docker               │
        └──────────────────────────────────┘
           │          │          │
           │          │          │
           ▼          ▼          ▼
     Open WebUI     n8n     VS Code Server
           │
           ▼
       Ollama Host
           │
           ▼
      Llama 3.2 Model

           │
           ▼
        Nginx Server
           │
           ▼
      Static Website
```

---

# 📦 Services

| Service        | Purpose             | Default Port |
| -------------- | ------------------- | ------------ |
| Open WebUI     | Chat Interface      | 3000         |
| n8n            | Workflow Automation | 5678         |
| VS Code Server | Browser IDE         | 8443         |
| Nginx          | Local Web Hosting   | 8080         |
| Ollama         | Local AI Engine     | 11434        |

---

# ⚡ Installation Overview

## 1. Install Ubuntu Server

* Install Ubuntu Server 24.04 LTS
* Enable OpenSSH
* Configure Network
* Create Admin User

---

## 2. Update System

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 3. Install Docker

```bash
curl -fsSL https://get.docker.com | sh
```

---

## 4. Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Run a lightweight model:

```bash
ollama run llama3.2:3b
```

---

## 5. Deploy Docker Services

```bash
docker compose up -d
```

---

# 🌐 Local Access

| Service    | URL                   |
| ---------- | --------------------- |
| Open WebUI | http://SERVER-IP:3000 |
| n8n        | http://SERVER-IP:5678 |
| VS Code    | http://SERVER-IP:8443 |
| Website    | http://SERVER-IP:8080 |

---

# 📈 Recommended Upgrade

For better performance:

* Upgrade RAM to **16GB**
* Use NVMe SSD
* Connect via Gigabit Ethernet
* Monitor resources using:

```bash
htop
```

or

```bash
docker stats
```

---

# 🎯 Use Cases

* AI Automation
* Local LLM Development
* Prompt Engineering
* AI Chatbot
* Self-hosted ChatGPT
* n8n Workflow Automation
* Web Development
* API Development
* Local Testing Environment
* Personal Cloud Lab
* Learning Docker
* Home Server

---

# 📸 Screenshots

> Add screenshots of:

* Ubuntu Server
* Open WebUI
* n8n Dashboard
* VS Code Server
* Docker Containers
* Ollama Models

---

# 🔒 Security Notes

* Change all default passwords.
* Enable UFW Firewall.
* Use SSH keys instead of passwords.
* Keep Docker images updated.
* Restrict public access if exposing services.

---

# 📚 Learning Goals

This project is ideal for developers who want to learn:

* Docker
* Linux Server Administration
* AI Infrastructure
* Self-Hosting
* Local LLM Deployment
* Workflow Automation
* DevOps Basics

---

# 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

Feel free to open an Issue or submit a Pull Request.

---

# 📄 License

This project is available under the **MIT License**.

---

# ⭐ Support

If this repository helped you, consider giving it a ⭐ on GitHub.

---

## 👨‍💻 Author

**Built with ❤️ for AI Automation, Self-Hosting, and Open Source.**
