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

- **Learn by Doing**: Deploy and explore a full **T-Pot honeynet** in Azure — hands-on experience with real honeypots in under an hour.  
- **Real Attack Data**: Observe live global attacks — **SSH brute force**, **SIP scanning**, **Suricata alerts**, and more — within 24 hours of deployment.  
- **All-in-One Threat Lab**: No external SIEM needed — **T-Pot** includes **Elasticsearch**, **Kibana**, **CyberChef**, **Elasticvue**, and **SpiderFoot** for log analysis, visualization, and OSINT.  
- **

Educational & Safe**: Fully isolated Ubuntu VM, low-cost (~$5–10/month), and easy to tear down — perfect for learning attacker tactics without risk.

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
