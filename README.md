# 🛡️ Healthcare Threat Detection Tool (HTDT)

This repository documents the final configuration and setup for my graduation project: **HTDT – Healthcare Threat Detection Tool**. The system simulates a real-world healthcare environment to detect threats targeting medical IoT devices, EHR systems (OpenEMR), and medical imaging servers (DICOM), using Wazuh, Suricata, and the ELK stack.

## 📁 Virtual Machines & Setup

**Download all VMs from OneDrive:**  
🔗 [HTDT VMs Folder](https://elsewedyedu1-my.sharepoint.com/:f:/g/personal/me2101233_tkh_edu_eg/EmMPV4s_kfNMjfANZ7tYly4BRvLhsWNZZyonIoeRVfsdvg?e=QAzEoZ)

The setup contains 5 VirtualBox VMs:

| VM | Role | Tools Installed |
|----|------|------------------|
| **VM1** | OpenEMR + Orthanc DICOM Server | Wazuh Agent |
| **VM2** | IoT Devices + ELK Stack | Filebeat, Elasticsearch, Logstash, Kibana |
| **VM3** | Wazuh Manager | Wazuh Server |
| **VM4** | Attacker Machine | Kali Linux, Metasploit, Nmap, Hydra |
| **VM5** | IDS Server | Suricata, Filebeat |

---

## 🏗️ System Architecture

![HTDT System Architecture](diagram.png)  
*Architecture shows how VMs interact with IDS, Wazuh, and the ELK stack to detect threats in a healthcare environment.*

---

## ⚙️ Configuration File Locations

### ✅ VM1 – OpenEMR + Orthanc DICOM

- Wazuh Agent:  
  `/var/ossec/etc/ossec.conf`
  
- Apache Logs (monitored):  
  `/var/log/apache2/access.log`  
  `/var/log/apache2/error.log`

---

### ✅ VM2 – IoT Devices + ELK Stack

- Filebeat:  
  `/etc/filebeat/filebeat.yml`

- Logstash Pipeline:  
  `/etc/logstash/conf.d/logstash.conf`

- Kibana Dashboards:  
  Accessible via `http://<vm-ip>:5601`

---

### ✅ VM3 – Wazuh Manager

- Wazuh Config:  
  `/var/ossec/etc/ossec.conf`

- Custom Rules:  
  `/var/ossec/etc/rules/local_rules.xml`

- Log Output:  
  `/var/ossec/logs/ossec.log`

---

### ✅ VM4 – Attacker (Kali Linux)

- Nmap, Hydra, Hping3, Metasploit:  
  Tools used from native locations:
  - `/usr/bin/nmap`
  - `/usr/bin/hydra`
  - `/usr/sbin/hping3`
  - `/usr/share/metasploit-framework/`

---

### ✅ VM5 – Suricata IDS

- Suricata Main Config:  
  `/etc/suricata/suricata.yaml`

- Rule Files:  
  `/etc/suricata/rules/`

- Log Output:  
  `/var/log/suricata/eve.json`  
  `/var/log/suricata/stats.log`

- Filebeat (Forward to ELK):  
  `/etc/filebeat/filebeat.yml`

---

## 🧪 Simulated Attacks

- **DoS attack** using `hping3` on medical IoT devices
- **Brute-force attack** using `hydra` on OpenEMR login
- **Port scan** with `nmap` to enumerate services
- **Metasploit shell** to demonstrate potential exploitation

Each attack was logged, detected, and visualized in real-time through Kibana dashboards and Wazuh alerts.

---

## 📊 Visualisation & Alerting

- Real-time dashboard built in **Kibana**
- Alerts correlated in **Wazuh**
- Logs stored and searchable via **Elasticsearch**

---

## 📎 Report

Please refer to the full academic report submitted alongside this project for deeper technical explanations, results, and evaluations.

---

## 📬 Contact

**Mohamed H. Ezzat**  
Cyber Security BSc – Coventry University (TKH)  
Email: me2101233@tkh.edu.eg

---

