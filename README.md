# Personal-SOC-Lab-Wazuh
Dự án xây dựng SOC Lab cá nhân sử dụng giải pháp Wazuh SIEM + EDR để giám sát an toàn thông tin endpoint (Windows/Linux) và phân tích cảnh báo tấn công thời gian thực.
# 🛡️ Personal SOC Lab Implementation (Wazuh SIEM & EDR)

## 📌 Project Overview
This project demonstrates the deployment and configuration of a centralized **Security Operations Center (SOC)** lab environment utilizing **Wazuh (SIEM/XDR)**. The primary objective is to gain hands-on experience in security telemetry collection, log analysis, active response, and incident detection across diverse enterprise endpoints (Windows and Linux).

---

## 🌐 Network Topology & Architecture
The lab environment simulates a corporate network infrastructure using virtualized machines interconnected via a host-only/NAT network adapter.

### 🖥️ Core Components:
*   **Wazuh Manager (Ubuntu Server 22.04 LTS):** Functions as the centralized SIEM engine responsible for log parsing, rule matching, and alert generation.
*   **Windows Endpoint (Windows 10/11):** Monitored workstation equipped with Sysmon and Wazuh Agent.
*   **Linux Endpoint (Ubuntu Desktop):** Monitored server/workstation equipped with Wazuh Agent.
*   **Attacker (Kali Linux / Host OS):** Machine used to simulate real-world attack vectors.

---

## 🚀 Deployment & Installation Steps

### Phase 1: SIEM Server Setup
1. Deployed an Ubuntu Server instance (4GB RAM, 2 vCPUs).
2. Executed the Wazuh all-in-one installation script:
   ```bash
   curl -sO https://wazuh.com && sudo bash wazuh-install.sh -a
   ```
3. Verified access to the Web UI dashboard via `https://<Wazuh-Manager-IP>`.

### Phase 2: Endpoint EDR Agent Deployment
*   **Windows:** Installed the Wazuh Windows MSI agent via administrative PowerShell, integrated Sysmon for deep process auditing, and started the `Wazuh` service.
*   **Linux:** Configured repository endpoints, installed the `wazuh-agent` package, and enrolled it to the manager IP.

---

## 💥 Simulated Attack & Detection Use Cases

### 1. SSH / RDP Brute Force Detection
*   **Attack Vector:** Executed a high-frequency dictionary attack using `Hydra` against the exposed SSH/RDP port on the target endpoint.
*   **SIEM Detection:** The Wazuh ruleset successfully identified the threshold of anomalous authentication failures, triggering a **Level 10 Critical Alert** (Rule ID: `5712` / `18130`).

### 2. Malicious Process Execution (Mimikatz / Privilege Escalation)
*   **Attack Vector:** Simulated credential dumping techniques on the Windows host.
*   **SIEM Detection:** Detected through integration with Windows Security Logs and Sysmon Event ID 1 (Process Creation).

---

## 📊 Key Achievements & Takeaways
*   Successfully mastered **Log Aggregation** from multiple operating systems into a single glass pane.
*   Gained profound familiarity with **Windows Event Logs** (Security, System, Application) and **Linux Syslog**.
*   Understood how threat behaviors are translated into actionable, rule-based alerts within a corporate SOC matrix.

---

## 👤 Contact & Links
*   **Author:** Thanh Nhan
*   **LinkedIn:** 
*   **Email:** lttnhan2707@gmail.com
