# moskalprzemyslaw.github.io
Cybersecurity &amp; SOC Analyst Homelab Documentation


# Building My SOC Homelab 

Welcome to my cybersecurity homelab project! I started this lab to get practical, hands-on experience with system hardening, SIEM platforms, log analysis, and threat detection.

Here is how I built the entire environment step by step.
---
## 1. Hardware & Operating System
I repurposed an old Dell OptiPlex PC into a dedicated 24/7 Linux server.

* **OS:** Ubuntu Server 24.04 LTS
* **Setup:** Headless configuration 100% managed via SSH from Windows Terminal.
* **Network:** Assigned a static IP 192.168.0.106 on my local network for reliable access.
---
## 2. Initial Setup 
Before deploying any security tools, I secured the host:

1. **System Updates:** Updated repositories and packages (`apt update && apt upgrade`).
2. **Firewall (UFW):**
   * Blocked all incoming traffic by default "default deny incoming".
   * Allowed outgoing traffic "default allow outgoing".
   * Whitelisted port "22" for SSH remote access.
3. **Brute-Force Defense:** Installed and enabled **Fail2ban** to automatically detect and ban failed SSH login attempts.
4. **Kernel Tuning:** Increased "vm.max_map_count=262144" in "/etc/sysctl.conf" to meet memory requirements for log indexing.
---
## 3. Deploying Wazuh SIEM with Docker

I chose Docker to keep services isolated and lightweight:

1. Installed Docker Engine and Docker Compose.
2. Cloned the Wazuh repository and generated local SSL certificates.
3. Allowed port "443" (HTTPS) through UFW for the web dashboard.
4. Spun up the entire Wazuh stack using Docker Compose.

The SIEM dashboard is now live and accessible at `https://192.168.0.106`.

---
