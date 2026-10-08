# Wi-Fi Security Audit using Aircrack-ng

A hands-on cybersecurity project focused on auditing the security of an authorized Wi-Fi network using Kali Linux, Aircrack-ng and Wireshark.

## 📌 Overview

Wi-Fi networks are an important part of modern computer networks, but improperly configured or weakly protected wireless networks can become security risks.

This project demonstrates the process of performing a controlled Wi-Fi security audit in an authorized lab environment.

The project covers wireless network discovery, monitor mode, traffic capture, authentication analysis and password security auditing.

## 🎯 Objectives

- Understand basic Wi-Fi security concepts.
- Learn how monitor mode works.
- Discover wireless networks in a controlled environment.
- Understand BSSID, SSID and wireless channels.
- Capture and analyze wireless authentication traffic.
- Understand WPA/WPA2 authentication.
- Use Aircrack-ng for security auditing.
- Analyze captured traffic using Wireshark.
- Identify weaknesses in wireless password security.
- Provide security recommendations.

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Kali Linux | Security testing environment |
| Aircrack-ng | Wireless security auditing |
| Airodump-ng | Wireless network discovery and packet capture |
| Wireshark | Packet analysis |
| Linux Terminal | Command-line operations |
| USB Wi-Fi Adapter | Wireless monitoring |

## 🖥️ Lab Environment

- Operating System: Kali Linux
- Environment: Virtual Machine / Physical System
- Wi-Fi Adapter: Monitor-mode compatible adapter
- Target: Authorized lab Wi-Fi network
- Security Testing: Controlled environment

## 📚 Concepts Covered

### 1. Wireless Network Discovery

Identifying nearby wireless networks and understanding information such as:

- SSID
- BSSID
- Channel
- Signal strength
- Encryption type

### 2. Monitor Mode

Monitor mode allows a compatible wireless adapter to observe wireless frames without operating like a normal connected Wi-Fi client.

### 3. WPA/WPA2 Authentication

The project studies the authentication process between a wireless client and an access point, including the concept of the WPA/WPA2 four-way handshake.

### 4. Packet Capture

Wireless traffic is captured in a controlled lab environment for security analysis.

### 5. Password Security Auditing

Captured authentication information can be used to evaluate the strength of an authorized network password against candidate passwords.

### 6. Packet Analysis

Wireshark is used to inspect captured network traffic and understand wireless communication.

## 🔍 Methodology

The project follows these major stages:

```text
Wireless Interface
       ↓
Monitor Mode
       ↓
Network Discovery
       ↓
Authorized Lab Network Selection
       ↓
Authentication Traffic Capture
       ↓
Packet Analysis
       ↓
Password Security Audit
       ↓
Security Recommendations