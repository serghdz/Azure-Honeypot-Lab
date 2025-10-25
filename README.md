# Azure Honeypot Lab – GitHub Repository

Welcome to the **Azure Honeypot Lab** documentation repository! This project archives my two-part blog series on building and analyzing a realistic honeypot in Microsoft Azure, originally published on [ChekoBytes](https://chekobytes.com).

The lab simulates a vulnerable web server to attract and log real-world attacker behavior — all in a safe, isolated environment. Perfect for security researchers, blue teamers, and cloud enthusiasts.

---

## Overview

This repo contains **two separate Markdown files**, each corresponding to one part of the series:

| Part | File | Title | Summary |
|------|------|-------|---------|
| **Part 1** | [`azure-honeypot-lab-pt-1.md`](https://github.com/serghdz/Azure-Honeypot-Lab/blob/main/Documentation/azure-honeypot-lab-pt-1.md) | [Setting Up a Vulnerable Web Server in Azure](https://chekobytes.com/posts/azure-honeypot-lab-pt-1) | Covers Azure VM setup, installing a deliberately vulnerable PHP app, firewall rules, SSH hardening, and initial logging with `auth.log` and `nginx` access logs. |
| **Part 2** | `azure-honeypot-lab-pt-2.md` | [Capturing Attacks & Analyzing Logs](https://chekobytes.com/posts/azure-honeypot-lab-pt-2) | Dives into log forwarding with **Azure Monitor Agent**, centralizing data in **Log Analytics Workspace**, building KQL queries to detect brute force, web shells, and exploit attempts, plus attacker IP geolocation and timeline visualization. |

---

## Why This Project?

- **Learn by Doing**: Hands-on cloud security lab you can replicate in under an hour.
- **Real Attack Data**: See actual SSH brute force, SQLi probes, and directory traversal attempts within 24 hours.
- **Azure-Native Tools**: No third-party SIEM required — uses built-in Azure security services.
- **Educational & Safe**: Fully isolated, low-cost (~$10/month), and easy to tear down.

---

## Key Learnings

- How attackers scan and exploit misconfigured cloud assets
- Using **Kusto Query Language (KQL)** for threat hunting
- Setting up **data collection rules** and **diagnostic settings**
- Parsing unstructured logs (`auth.log`, `nginx`) in the cloud
- Visualizing attack patterns with Azure dashboards

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
