# Healthcare Threat Detection Tool (HTDT) – Final Submission

This repository contains the configuration files and documentation for the **Healthcare Threat Detection Tool (HTDT)** developed as part of the Cyber Security Project at TKH/Coventry University.

The HTDT simulates a healthcare infrastructure to detect cyber threats using open-source tools. The system includes real-time monitoring, log analysis, and visualization for EMR systems, IoT devices, and DICOM servers.

---

## 📦 Virtual Machines (Download)

All VM files used in this project are hosted on OneDrive:

🔗 [Access VirtualBox VMs Folder]([https://elsewedyedu1-my.sharepoint.com/:f:/g/personal/me2101233_tkh_edu_eg/EmMPV4s_kfNMjfANZ7tYly4BRvLhsWNZZyonIoeRVfsdvg?e=lKHZid](https://elsewedyedu1-my.sharepoint.com/:f:/g/personal/me2101233_tkh_edu_eg/EmMPV4s_kfNMjfANZ7tYly4BRvLhsWNZZyonIoeRVfsdvg?e=PyPU2k))

> 📝 The folder includes 5 VMs used in the setup (OpenEMR, IoT+ELK, Wazuh Manager, Suricata, Attacker - Kali Linux). Each VM is named clearly for identification.

---

## 🖥️ System Overview

**Architecture:**
- Suricata – Network-based IDS (VM5)
- Wazuh – Host-based monitoring and compliance (VM3 + agents on VM1, VM2)
- ELK Stack – Data parsing and visualization (VM2)
- OpenEMR + Orthanc DICOM – Target services (VM1)
- IoT Device Simulation – Custom traffic (VM2)
- Kali Linux Attacker – Simulates attacks (VM4)

---

## ⚙️ Key Configuration Files

These config files are located within their respective VMs (listed inside each VM folder):

### 🛡 Suricata (VM5)
- `suricata.yaml` – Core ruleset and interface config
- `eve.json` – Alert output log
- `filebeat.yml` – Log forwarding to Logstash

### 📄 Wazuh (VM1, VM2, VM3)
- `ossec.conf` – Agent and Manager configuration
- Custom rules – Detect brute-force logins, service anomalies
- Compliance module – HIPAA alerting rules

### 📊 ELK Stack (VM2)
- `logstash.conf` – Input/output pipeline for Suricata & Wazuh logs
- `grok` filters – Parsing formats for Suricata and Wazuh alerts
- Kibana Dashboards – Prebuilt visualizations (network threats, endpoint events, GeoIP maps)

---

## 🧪 Simulated Attacks
Executed from Kali (VM4):
- 🔍 Nmap – Port Scanning
- 💥 Hping3 – DoS Flooding
- 🔐 Hydra – Brute-force login
- 🛠 Metasploit – Payload delivery (tested)

---

## 📝 Notes
- All testing was done in a **closed virtual network** for safety and ethics compliance.
- No real patient data was used; dummy records were applied in OpenEMR.
- All machines are configured with **static IPs** and bridged adapters for full visibility.

---

## 🧠 Instructions
1. Download the VM files from the OneDrive link above.
2. Import into **Oracle VirtualBox** using `Machine > Add` or open `.vbox` files.
3. Start with the Wazuh Manager, then boot all other machines.
4. Ensure all VMs are on the same bridged adapter network.
5. Launch Kibana (`http://192.168.1.21:5601`) for dashboards.
6. Run test attacks from the Kali VM to validate alerting.

---

## 📞 Contact
**Mohamed H. Ezzat**  
Email: me2101233@tkh.edu.eg  
Student ID: 202101233  
Supervisor: Dr. Haitham Ghalwash  

---

