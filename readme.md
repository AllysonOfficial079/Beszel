## 📊 Beszel Docker Monitoring

A minimalist, lightweight, and real-time server monitoring hub designed for Docker environments. Beszel provides a clean, zero-bloat dashboard to track resources without straining your host system.

---

## 🚀 Why Beszel?

* **⚡ Ultra-Lightweight Agent** — Consumes minimal CPU and RAM ($< 15\text{MB}$), ensuring your system resources remain dedicated to your workloads.
* **🐋 Native Docker Tracking** — Automatically discovers containers and displays per-container CPU, memory, and I/O metrics.
* **⏱️ Real-Time Dashboards** — Sub-second metric rendering for immediate visibility into performance spikes and resource utilization.
* **🔒 Self-Hosted & Secure** — Keep your infrastructure data entirely under your control with local Docker deployments.
* **🔔 Instant Alerting** — Configure smart triggers for resource thresholds and receive notifications via Webhooks, Discord, or Telegram.

---

## 🛠️ Quick Start (Docker Compose)

Launch the Beszel Hub and Agent instantly using the minimalist configuration below:

Code output
README.md successfully created.

```yaml
version: '3.8'

services:
  beszel-hub:
    image: henrygd/beszel:latest
    container_name: beszel-hub
    restart: unless-stopped
    ports:
      - "8090:8090"
    volumes:
      - ./beszel-data:/app/data

  beszel-agent:
    image: henrygd/beszel-agent:latest
    container_name: beszel-agent
    restart: unless-stopped
    environment:
      - PORT=4567
      - KEY=your_agent_public_key_here
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
⚙️ Configuration
Access the Dashboard: Open http://localhost:8090 to create your admin account.

Add a System: Copy the generated public key from the Hub UI.

Deploy the Agent: Paste the key into your Agent's KEY environment variable and start the container.
"""
