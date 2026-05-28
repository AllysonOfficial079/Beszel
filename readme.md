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

# Step 1 
Launch the Beszel Hub Below using the code:
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
⚙️ Configuration
Access the Dashboard: Open http://localhost:8090 to create your admin account.

Add a System: Copy the generated public key from the Hub UI.

Deploy the Agent: Paste the key into your Agent's KEY environment variable and start the container.
Code output
README.md successfully created.
This is for the Hub Which you need to create a Custom Stack in Portainer for (Be sure to install Docker first)
"""
```
# Step 2
Launch the Beszel Agent Below using the code: 
```yaml
services:
  beszel-agent:
    image: henrygd/beszel-agent
    container_name: beszel-agent
    restart: unless-stopped
    network_mode: host
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - /portainer/Files/AppData/Config/beszel_agent_data:/var/lib/beszel-agent
      # monitor other disks / partitions by mounting a folder in /extra-filesystems
      # - /mnt/disk/.beszel:/extra-filesystems/sda1:ro
    environment:
      LISTEN: 45876
      KEY: 'This Key is generated after you setup the hub and add a system'
      TOKEN: Created after you created a system and set it up in the hub
      HUB_URL: http://localhost:8090

"""
