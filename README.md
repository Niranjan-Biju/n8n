# 🧩 My n8n Automation Projects

**[n8n](https://n8n.io)** is an open-source, self-hostable automation platform that lets you visually connect APIs, services, and logic — no coding required.

This repository contains a collection of automation workflows built on my self-hosted n8n instance.

Check out my workflows **[here](./workflows)**

---

## 📂 Repository Structure

| File/Folder          | Purpose                                                  |
|----------------------|----------------------------------------------------------|
| `setup.md`           | Step-by-step guide to setting up n8n using WSL2 + Docker |
| `workflows/`         | Contains exported `.json` workflows                      |
| `screenshots/`       | Contains screenshots of the workflows                    |
| `docker-compose.yml` | Full Docker stack: n8n + PostgreSQL + Ollama             |

## 🛠️ Projects

### 1️⃣ RSS-to-Email Tech Digest

This workflow automates the process of reading tech news by fetching articles from an  RSS feed, filters for a category, summarises the top items using an AI Model, and sending a clean, HTML-formatted digest to email.

- **Trigger:** Scheduled daily
- **Source:** TechCrunch RSS feed
- **Filter:** Articles with categories like "AI startups"
- **AI Agent:** Gemini (used to summarize article content)
- **Output:** Clean, HTML-formatted email digest with links
- **Goal:** Automate news summarization into email-ready content

📄 Workflow file: [rss-digest.json](./workflows/rss-digest.json)

📸 Screenshot: [rss-email-output](./workflows/rss-email-output.png)

---
