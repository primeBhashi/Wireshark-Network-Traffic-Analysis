# Network Traffic Analysis & Security Posture Assessment

## 📌 Project Overview
This project focuses on the practical analysis of network traffic, protocol behaviors, and the identification of potential security vulnerabilities using **Wireshark** on **Kali Linux**. It serves as a foundational study in manual packet inspection, paving the way for advanced automated threat detection.

## 🛠️ Tools & Technologies Used
* **OS:** Kali Linux (VirtualBox Environment)
* **Network Analyzer:** Wireshark
* **Security Scanner:** Nmap
* **Protocols Analyzed:** HTTP, HTTPS, TCP, DNS

---

## 🔬 Phases of Analysis

### Phase 1: Baseline Traffic Capture & Interface Configuration
Configured the `eth0` interface in promiscuous mode to capture raw network frames. Established a baseline of normal network noise and background processes.

<img width="960" height="504" alt="capture packets" src="https://github.com/user-attachments/assets/bf1ab919-e0e5-49e6-ad1f-fa22b4c53f78" />



### Phase 2: Protocol Vulnerability Analysis (HTTP vs. HTTPS)
Demonstrated the critical security flaw in unencrypted protocols by performing a live capture of an HTTP login session.
* **Finding:** Successfully intercepted and extracted clear-text user credentials (Username & Password) using the `http.request.method == "POST"` filter, highlighting the necessity of TLS encryption.

<img width="960" height="504" alt="packet scan" src="https://github.com/user-attachments/assets/76b275b5-7ac1-4f2c-ba8d-2215737619a6" />


### Phase 3: TCP 3-Way Handshake & DNS Resolution
Conducted a deep-dive analysis into the core mechanics of web connectivity.
* Filtered DNS queries to identify target IP resolutions.
* Isolated and analyzed the fundamental TCP connection establishment process: `[SYN]`, `[SYN, ACK]`, and `[ACK]`.

<img width="960" height="504" alt="dns handshake" src="https://github.com/user-attachments/assets/61bab268-7c14-45de-b35c-281c821f3b9e" />


### Phase 4: Active Reconnaissance Detection (Malware/Attack Simulation)
Simulated a live network attack using Nmap (`nmap -p 1-100 scanme.nmap.org`) to observe how active reconnaissance manifests on the wire.
* **Finding:** Identified a distinct pattern of rapid, sequential connection attempts resulting in a flood of `[RST, ACK]` responses from closed ports. This pattern is a primary indicator of a Port Scan attack.
<img width="960" height="504" alt="nmap scan" src="https://github.com/user-attachments/assets/62413908-9a0a-433a-b01c-ca140675838c" />



---

## 🚀 Future Scope
This manual packet-level analysis establishes the groundwork for developing automated security solutions. The behavioral patterns and anomalies identified here (such as the high-frequency RST responses during reconnaissance) will be utilized as baseline detection rules for a **Python-Based Network Intrusion Detection System (NIDS)**, which will eventually be integrated with a **Real-Time ELK Dashboard** for centralized monitoring and alerting.
