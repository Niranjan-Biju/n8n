<h1> n8n </h1>
<hr style="height:2px; background-color:#ccc; border:none;">

This document outlines the full step-by-step process I followed to self-host ***n8n*** on my system using WSL2, Debian, and Docker Compose.

## ⚙️ My Environment

- Windows 11
- WSL2
- Debian (installed via WSL)
- Docker & Docker Compose
<hr style="height:2px; background-color:#ccc; border:none;">

## 🛠️ Step-by-Step Setup

### 1️⃣ Enable WSL & Install Debian

<pre>wsl --install -d Debian</pre>

**⚠️ Note: WSL will install Ubuntu by default**

### 2️⃣ Install Docker (Inside Debian)

<pre>curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io</pre>

### 3️⃣ Install Docker Compose

<pre>sudo apt install docker-compose-plugin</pre>

### 4️⃣ Docker Compose File (n8n + PostgreSQL + Ollama)

- Created a <code>docker-compose.yml</code> with:
  - n8n service
  - PostgreSQL
  - Qdrant
  - Ollama 
  - Named volumes for persistence

- Exposed n8n on port <code>5678</code>
- Configured volumes: <code>n8n_storage</code>, <code>postgres_storage</code>,<code> qdrant_storage</code>,<code> ollama_storage</code>
- Configured environment variables in docker-compose.yml

### 5️⃣ Start the Stack

<pre>docker compose up -d</pre>

### 6️⃣ First-Time Access

- Opened: http://localhost:5678
- Created initial user via n8n's UI
- Verified credentials

### 7️⃣ Stop the Entire Stack

- docker compose down
<hr style="height:2px; background-color:#ccc; border:none;">

**💡 Check running containers in docker: <code>docker ps</code>**

**💡 View n8n logs: <code>docker logs -f n8n</code>**
