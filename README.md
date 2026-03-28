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




### Phase 2: Protocol Vulnerability Analysis (HTTP vs. HTTPS)
Demonstrated the critical security flaw in unencrypted protocols by performing a live capture of an HTTP login session.
* **Finding:** Successfully intercepted and extracted clear-text user credentials (Username & Password) using the `http.request.method == "POST"` filter, highlighting the necessity of TLS encryption.



### Phase 3: TCP 3-Way Handshake & DNS Resolution
Conducted a deep-dive analysis into the core mechanics of web connectivity.
* Filtered DNS queries to identify target IP resolutions.
* Isolated and analyzed the fundamental TCP connection establishment process: `[SYN]`, `[SYN, ACK]`, and `[ACK]`.

*(👉 TCP handshake එක (SYN, SYN-ACK, ACK) තියෙන screenshot එක මෙතනට දාන්න)*

### Phase 4: Active Reconnaissance Detection (Malware/Attack Simulation)
Simulated a live network attack using Nmap (`nmap -p 1-100 scanme.nmap.org`) to observe how active reconnaissance manifests on the wire.
* **Finding:** Identified a distinct pattern of rapid, sequential connection attempts resulting in a flood of `[RST, ACK]` responses from closed ports. This pattern is a primary indicator of a Port Scan attack.

*(👉 අර රතු පාටින් RST packets පිරිලා තිබුණු Nmap scan screenshot එක මෙතනට දාන්න)*

---

## 🚀 Future Scope
This manual packet-level analysis establishes the groundwork for developing automated security solutions. The behavioral patterns and anomalies identified here (such as the high-frequency RST responses during reconnaissance) will be utilized as baseline detection rules for a **Python-Based Network Intrusion Detection System (NIDS)**, which will eventually be integrated with a **Real-Time ELK Dashboard** for centralized monitoring and alerting.
