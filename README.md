# 🖥️ Dell OptiPlex 3050 Home Lab Server

A comprehensive guide and configuration repository for deploying a power-efficient, self-hosted Home Lab server environment on a **Dell OptiPlex 3050 Micro**. Running **Ubuntu Server 24.04 LTS**, this setup orchestrates local AI models via **Ollama & Open WebUI**, workflow automation via **n8n**, cloud development via **code-server (VS Code Web)**, and static web hosting via **Nginx** using Docker Compose.

---

## 📐 Target Hardware Specifications

* **Model:** Dell OptiPlex 3050 Micro
* **CPU:** Intel Core i5-7500T (4 Cores @ 2.7 GHz)
* **RAM:** 8GB DDR4 *(16GB Recommended for running 7B/8B LLMs)*
* **Storage:** 256GB NVMe SSD
* **Network:** Gigabit Ethernet / Wi-Fi

---

## 🛠️ Software & Architecture Stack

* **Operating System:** Ubuntu Server 24.04 LTS
* **Container Engine:** Docker & Docker Compose
* **AI Engine:** Ollama (`llama3.2:3b` model running host-native for maximum CPU performance)
* **Containerized Services:**
  * **Open WebUI:** ChatGPT-style web interface for interacting with Ollama.
  * **n8n:** Self-hosted workflow automation platform.
  * **code-server:** Full VS Code IDE running directly in the browser.
  * **Nginx:** Lightweight web server hosting local static websites.

---

## 🚀 Step-by-Step Installation & Setup

### Step 1: Requirements & Prerequisites
* USB Flash Drive (8GB minimum capacity).
* USB Keyboard & Monitor (Required only for initial OS installation).
* Ethernet Cable (LAN connection recommended for server stability)[cite: 2].
* **Tools:** [Rufus](https://rufus.ie/) and [Ubuntu Server 24.04 LTS ISO](https://ubuntu.com/download/server)[cite: 2].

---

### Step 2: Installing Ubuntu Server OS
1. **Download:** Grab the Ubuntu Server 24.04 LTS ISO and download Rufus on a PC[cite: 2].
2. **Create USB:** Open Rufus, select your USB drive and Ubuntu ISO, then click **START**[cite: 2].
3. **Boot Setup:** Plug the USB into the OptiPlex 3050, power on, tap `F12` to enter the Boot Menu, and select the USB drive[cite: 2].
4. **Installer Steps:**
   * Select Language and Keyboard layout[cite: 2].
   * Select **Ubuntu Server** (Minimal/Standard)[cite: 2].
   * Configure Network and note down the assigned static/DHCP IP address (e.g., `192.168.0.100`)[cite: 2].
   * Storage: Select **Use an entire disk** (256GB NVMe SSD)[cite: 2].
   * User Setup: Create username (e.g., `admin`) and server hostname (e.g., `homelab`)[cite: 2].
   * **OpenSSH:** Ensure **Install OpenSSH Server** is checked[cite: 2].
5. Reboot after installation completes, unplug the USB, and disconnect the monitor/keyboard[cite: 2].

---

### Step 3: Initial Server Access & System Updates
From your laptop/desktop, connect headlessly via SSH[cite: 2]:

```bash
ssh admin@192.168.0.100

Update base packages and install essential utilities[cite: 2]:

Bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget git build-essential ufw
Step 4: Installing Docker & Docker Compose
Run the automated Docker script and grant non-root execution permissions[cite: 2]:

Bash
# Install Docker automatic script
curl -fsSL [https://get.docker.com](https://get.docker.com) -o get-docker.sh
sudo sh get-docker.sh

# Enable Docker without sudo
sudo usermod -aG docker $USER
newgrp docker
Step 5: Installing Ollama & Llama 3.2 Model
Install Ollama natively on the host machine to optimize CPU execution for AI models[cite: 2]:

Bash
curl -fsSL [https://ollama.com/install.sh](https://ollama.com/install.sh) | sh
💡 RAM Optimization Note: On an 8GB RAM system, run lightweight models such as llama3.2:1b or llama3.2:3b to maintain low memory overhead[cite: 2].

Pull the llama3.2:3b model[cite: 2]:

Bash
ollama run llama3.2:3b
Step 6: Deploying Docker Services
Create the deployment directory and configure docker-compose.yml[cite: 2]:

Bash
mkdir -p ~/homelab && cd ~/homelab
nano docker-compose.yml

Paste the following container orchestration layout into docker-compose.yml[cite: 2]:YAMLversion: '3.8'

services:
  # 1. Open WebUI (ChatGPT-style Interface for Ollama)
  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    container_name: open-webui
    restart: always
    ports:
      - "3000:8080"
    extra_hosts:
      - "host.docker.internal:host-gateway"
    environment:
      - OLLAMA_BASE_URL=[http://host.docker.internal:11434](http://host.docker.internal:11434)
    volumes:
      - open-webui-data:/app/backend/data

  # 2. n8n Automation Tool
  n8n:
    image: docker.n8n.io/n8nio/n8n:latest
    container_name: n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      - N8N_HOST=0.0.0.0
      - N8N_PORT=5678
      - N8N_PROTOCOL=http
    volumes:
      - n8n-data:/home/node/.n8n

  # 3. VS Code Web Edition (code-server)
  code-server:
    image: lscr.io/linuxserver/code-server:latest
    container_name: code-server
    restart: always
    ports:
      - "8443:8443"
    environment:
      - PUID=1000
      - PGID=1000
      - PASSWORD=YourStrongPasswordHere
    volumes:
      - code-server-config:/config
      - ~/projects:/config/workspace

  # 4. Local Web Server (Nginx)
  web-server:
    image: nginx:alpine
    container_name: web-server
    restart: always
    ports:
      - "8080:80"
    volumes:
      - ~/website:/usr/share/nginx/html:ro

volumes:
  open-webui-data:
  n8n-data:
  code-server-config:
Start all container services[cite: 2]:Bashdocker compose up -d

🌐 Web Services DirectoryAccess your applications via browser from any device on your local network[cite: 2]:Service NamePortAccess URL ExampleOpen WebUI (Llama UI)3000http://192.168.0.100:3000[cite: 2]n8n Workflows5678http://192.168.0.100:5678[cite: 2]VS Code Server8443http://192.168.0.100:8443[cite: 2]Local Web Hosting (Nginx)8080http://192.168.0.100:8080[cite: 2]📊 Resource Management & MaintenanceSystem Monitoring: Track real-time RAM and CPU consumption using htop or container usage with docker stats[cite: 2]:Bashhtop
docker stats
Static Site Hosting: Place your local static HTML/CSS/JS files inside the ~/website directory on the host server to serve them automatically via Nginx on port 8080[cite: 2].RAM Upgrade Path: While 8GB RAM handles Ubuntu, Docker, and lightweight 3B AI models smoothly, upgrading to 16GB RAM is recommended for multi-user execution and running larger 7B/8B models[cite: 2].Maintained on a Dell OptiPlex 3050 Micro Home Lab.
