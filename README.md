# 🔍 Wireshark SOC Lab: Identify the Attacker's IP

![Wireshark](https://img.shields.io/badge/Tool-Wireshark-blue?logo=wireshark)
![Category](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Focus](https://img.shields.io/badge/Focus-Network%20Traffic%20Analysis-green)
![Lab](https://img.shields.io/badge/Type-Hands--On%20SOC%20Lab-orange)

## 📌 Project Overview

This project demonstrates a practical network traffic investigation using **Wireshark**, a network protocol analyzer.

The scenario involved investigating unusual network traffic reported on a company's web server. Acting as a SOC analyst, I captured and analyzed network packets to identify the suspicious source IP address, examine TCP connection attempts, and determine the type of network activity.

The investigation identified a TCP SYN port scan originating from a suspicious host.

## 🎯 Project Objectives

- Capture and analyze network traffic using Wireshark.
- Understand TCP three-way handshake behavior.
- Apply Wireshark display filters.
- Identify suspicious source and destination IP addresses.
- Investigate TCP SYN requests.
- Identify open and closed server ports.
- Recognize indicators of a TCP SYN port scan.

## 🛠️ Tools and Technologies

| Tool | Purpose |
|---|---|
| Wireshark | Network packet capture and analysis |
| Windows | Lab environment |
| TCP/IP | Network communication analysis |
| Display Filters | Investigating suspicious packets |

## 🔬 Investigation Methodology

### Step 1: Capture Network Traffic

Started the Wireshark application and captured network traffic from the available Wi-Fi interface.

**Result:** 309 packets captured.

### Step 2: Filter TCP SYN Packets

Applied the following Wireshark display filter:

```wireshark
tcp.flags.syn == 1
```

This filter displays TCP packets where the SYN flag is set.

**Result:** 73 packets displayed.

### Step 3: Identify the Suspicious Source IP

Analyzed the Source column and identified an IP address repeatedly sending TCP SYN requests to the server.

**Suspicious source IP:** `192.168.10.66`

### Step 4: Identify the Target Server

Examined the Destination column to identify the server receiving the connection attempts.

**Target IP:** `192.168.10.20`

### Step 5: Investigate TCP Source Port

Inspected the TCP header and identified the repeated source port shown in the packets.

**Source port:** `52311`

### Step 6: Analyze Port Scanning Activity

Investigated the suspicious host's connection attempts against different destination ports.

**Result:** 40 different destination ports were tested.

### Step 7: Identify Open Ports

Analyzed the server responses and identified the ports that responded with SYN, ACK.

**Open ports:**
- 22 – SSH
- 80 – HTTP
- 443 – HTTPS

### Step 8: Identify Closed Ports

Observed the server's response to unsuccessful connection attempts.

**Closed-port response:**

```text
RST, ACK
```

This indicates that the connection attempt was rejected because the destination port was closed.

### Step 9: Calculate Closed Ports

Total ports tested: 40

Open ports: 3

Closed ports: 37

### Step 10: Determine the Attack Type

Based on repeated TCP SYN connection attempts against multiple destination ports, the activity was identified as a:

**TCP SYN Port Scan**

## 📊 Final Investigation Results

| Indicator | Finding |
|---|---|
| Total captured packets | 309 |
| Displayed SYN packets | 73 |
| Suspicious IP | 192.168.10.66 |
| Target server | 192.168.10.20 |
| Source port observed | 52311 |
| Destination ports tested | 40 |
| Open ports | 22, 80, 443 |
| Closed ports | 37 |
| Attack classification | TCP SYN Port Scan |

## 📸 Screenshots and Evidence

Screenshots from the practical investigation are available in the `screenshots/` directory.

They document the packet capture, TCP filtering, suspicious IP identification, port analysis, and final attack classification.

## 🧠 Key Learning Outcomes

Through this hands-on lab, I improved my understanding of:

1. How network packets travel between devices.
2. How to investigate suspicious network traffic.
3. How TCP SYN and RST/ACK flags work.
4. How to use Wireshark display filters.
5. How to identify potential port scanning activities.
6. How SOC analysts investigate network-based security events.

## 🛡️ Conclusion

This practical exercise demonstrated how Wireshark can help security analysts investigate suspicious network activities and identify potential reconnaissance attempts.

The investigation successfully identified `192.168.10.66` as the suspicious source, `192.168.10.20` as the target server, and TCP SYN port scanning as the observed activity.

**Learning by doing. Building practical cybersecurity skills one lab at a time.**

---

**Disclaimer:** This project was performed in an authorized educational lab environment. The IP addresses and findings are from the provided lab exercise and should not be interpreted as evidence of a real-world attack.

**#CyberSecurity #Wireshark #SOCAnalyst #NetworkSecurity #PacketAnalysis #BlueTeam #CyberSecurityLab**
