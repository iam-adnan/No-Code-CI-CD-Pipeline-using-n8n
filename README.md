# 🚀 Custom CI/CD Pipeline Engine using n8n

Welcome to my custom Continuous Integration and Continuous Deployment (CI/CD) project! Instead of using off-the-shelf tools like GitHub Actions or Jenkins, I built a bespoke automation engine from scratch using **n8n**, **Docker**, **Bash**, and **Webhooks**.

This project demonstrates event-driven architecture, infrastructure as code, server management, and automated alerting.

## 🏗️ Architecture Overview

The pipeline acts as the "brain" of the deployment process. It listens for code changes, securely logs into the production server, runs automated tests, builds a new Docker container, deploys it, and sends a status report to my communication channels.

[Image of n8n CI/CD pipeline workflow diagram]

### The Tech Stack:
* **Orchestration Engine:** Self-hosted n8n
* **Version Control:** GitHub (with Webhooks)
* **Containerization:** Docker & Docker Compose
* **Server Infrastructure:** Ubuntu Linux VPS
* **Alerting:** Slack / Discord API Integrations

---

## ⚙️ The Pipeline Flow (Visualized)

Here is how the n8n workflow routes the data:

```text
                                                                  🟢 (Tests Passed) ---> [ Notification: ✅ Success! ]
                                                                 /
[ GitHub Webhook ] ---> [ Check Branch: 'main' ] ---> [ SSH Server Execution ] 
                                                                 \
                                                                  🔴 (Tests Failed) ---> [ Notification: ❌ Error! ]
