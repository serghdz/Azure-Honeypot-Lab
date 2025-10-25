# Azure Honeypot Lab – GitHub Repository
 ---
 
Welcome to the **Azure Honeypot Lab** documentation repository! This project archives my two-part blog series on building and analyzing a realistic honeypot in Microsoft Azure, originally published on [ChekoBytes](https://chekobytes.com).

The lab simulates a vulnerable web server to attract and log real-world attacker behavior — all in a safe, isolated environment. Perfect for security researchers, blue teamers, and cloud enthusiasts.

---

## Overview

This repo contains **two separate Markdown files**, each corresponding to one part of the series:

| Part | File | Title | Summary |
|------|------|-------|---------|
| **Part 1** | [`azure-honeypot-lab-pt-1.md`](https://github.com/serghdz/Azure-Honeypot-Lab/blob/main/Documentation/azure-honeypot-lab-pt-1.md) | [Deploying T-Pot Honeypot in Azure](https://chekobytes.com/posts/azure-honeypot-lab-pt-1) | Walks through provisioning an **Ubuntu VM in Azure**, cloning and installing the **T-Pot honeynet platform** (a Dockerized suite of 20+ honeypots including Cowrie, Dionaea, Honeytrap, and Suricata), securing SSH with key-based auth and Fail2Ban, configuring **NSG firewall rules** to expose only attack surfaces, and verifying access to the **T-Pot web GUI** over HTTPS. |
| **Part 2** | [`azure-honeypot-lab-pt-2.md`](https://github.com/serghdz/Azure-Honeypot-Lab/blob/main/Documentation/azure-honeypot-lab-pt-2.md) | [Exploring T-Pot Dashboards & Threat Intelligence Tools](https://chekobytes.com/posts/azure-honeypot-lab-pt-2) | Deep dive into **T-Pot’s built-in visualization and analysis tools**: real-time **Attack Map** showing global attacker origins and honeypot hits; **CyberChef** for decoding payloads (e.g., ROT13); **Elasticvue** for querying **Elasticsearch indices**, inspecting **Suricata alerts** and **Cowrie sessions** in JSON; **Kibana dashboards** for filtering events by honeypot, port, or IP; and **SpiderFoot OSINT scans** to enrich attacker IPs with reputation, geolocation, and correlated entities — all powered by T-Pot’s internal ELK stack. |
---

## Why This Project?

- **Learn by Doing**: Hands-on cloud security lab you can replicate in under an hour.
- **Real Attack Data**: See actual SSH brute force, SQLi probes, and directory traversal attempts within 24 hours.
- **Azure-Native Tools**: No third-party SIEM required — uses built-in Azure security services.
- **Educational & Safe**: Fully isolated, low-cost (~$10 - 5/month), and easy to tear down.

---


## License

This work is licensed under [**CC BY-NC-SA 4.0**](https://creativecommons.org/licenses/by-nc-sa/4.0/)  
*Attribution — Non-Commercial — ShareAlike*

---

*Last updated: October 25, 2025*  
**Author**: [ChekoBytes](https://chekobytes.com)  
**Original Posts**:  
→ [Part 1](https://chekobytes.com/posts/azure-honeypot-lab-pt-1)  
→ [Part 2](https://chekobytes.com/posts/azure-honeypot-lab-pt-2)
