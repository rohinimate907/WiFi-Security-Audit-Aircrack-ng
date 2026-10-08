# Wi-Fi Security Audit Methodology

## 1. Introduction

This project performs a controlled security audit of an authorized Wi-Fi network using Kali Linux and the Aircrack-ng wireless security toolkit.

The purpose of the audit is to understand how wireless networks can be discovered, monitored, analyzed, and evaluated for common security weaknesses.

All testing is performed only on a network for which permission has been obtained.

---

## 2. Lab Environment

The security audit is performed in a controlled laboratory environment.

### Environment

- **Operating System:** Kali Linux
- **Wireless Security Toolkit:** Aircrack-ng
- **Packet Analysis Tool:** Wireshark
- **Wireless Adapter:** Monitor-mode compatible Wi-Fi adapter
- **Target:** Authorized laboratory Wi-Fi network

---

## 3. Methodology Overview

The complete methodology consists of the following stages:

```text
Wireless Adapter Identification
            ↓
      Monitor Mode
            ↓
    Wireless Discovery
            ↓
 Authorized Network Selection
            ↓
 Authentication Traffic Capture
            ↓
     Packet Analysis
            ↓
  Password Security Audit
            ↓
 Security Recommendations
```

---

## 4. Stage 1 — Wireless Interface Identification

The first step is to identify the wireless interface available in Kali Linux.

The wireless interface is required for performing wireless security auditing.

The interface name may vary depending on the operating system, hardware, and driver.

Typical interface names include:

- `wlan0`
- `wlan1`

The available interfaces are checked before starting the audit.

---

## 5. Stage 2 — Monitor Mode

After identifying the wireless adapter, the adapter is configured for monitor mode.

### What is Monitor Mode?

Monitor mode is a wireless interface mode that allows the adapter to observe wireless frames in its surrounding radio environment.

Unlike normal managed mode, the adapter does not need to be connected to a specific wireless network to observe wireless traffic.

Monitor mode is important for wireless security analysis because it allows wireless frames to be captured for analysis.

---

## 6. Stage 3 — Wireless Network Discovery

Once monitor mode is enabled, the wireless environment is scanned using the Aircrack-ng toolkit.

The discovery process provides information about available wireless access points.

Important information includes:

| Information | Description |
|---|---|
| SSID | Name of the Wi-Fi network |
| BSSID | MAC address identifying the access point |
| Channel | Wireless channel used by the network |
| Signal | Approximate signal strength |
| Encryption | Security mechanism used by the network |

Only the authorized laboratory network is selected for further testing.

---

## 7. Stage 4 — Authorized Target Selection

After discovering wireless networks, the target network for the security audit is identified.

The target must be:

- Owned by the tester, or
- Explicitly authorized for security testing.

The following information is recorded for the authorized laboratory network:

- SSID
- BSSID
- Channel
- Security protocol

Other nearby networks are not targeted or tested.

---

## 8. Stage 5 — Authentication Traffic Capture

The next stage involves monitoring the authorized laboratory network for authentication-related wireless traffic.

For WPA/WPA2 networks, clients and access points perform a four-way handshake during authentication.

### Simplified Four-Way Handshake

```text
Access Point                 Client
     |                          |
     | ---- Message 1 --------> |
     | <---- Message 2 -------- |
     | ---- Message 3 --------> |
     | <---- Message 4 -------- |
     |                          |
        Authentication
```

The captured authentication information does not contain the Wi-Fi password in plaintext.

Instead, it provides information that can be used during authorized password-security testing.

---

## 9. Stage 6 — Capture File

The wireless traffic captured during the audit is stored in a capture file.

Common capture formats include:

- `.cap`
- `.pcap`
- `.pcapng`

The capture file can later be analyzed using wireless security tools and packet analysis software.

For security and privacy reasons, real personal Wi-Fi captures should not be uploaded to a public GitHub repository.

---

## 10. Stage 7 — Packet Analysis with Wireshark

Wireshark is used to analyze captured network traffic.

The analysis helps understand:

- Wireless management frames
- Authentication-related traffic
- Network protocols
- Packet structure
- Source and destination information
- Communication patterns

Wireshark provides a graphical interface for examining individual packets and understanding how wireless communication occurs.

---

## 11. Stage 8 — Password Security Audit

After obtaining valid authentication information from the authorized laboratory network, password security can be evaluated using candidate passwords.

A wordlist contains possible password candidates.

The auditing process conceptually works as follows:

```text
Captured Authentication Data
             +
       Password Candidates
             ↓
       Candidate Testing
             ↓
       Authentication Match
```

If a weak password is present in the candidate list, it may be identified during the authorized audit.

A strong password that is not present in the tested candidate set may not be identified.

Therefore, the result of a dictionary-based audit should not be interpreted as proof that a password is absolutely secure.

---

## 12. Stage 9 — Security Evaluation

After completing the audit, the security configuration of the authorized network is evaluated.

The following factors are considered:

- Wireless encryption protocol
- Password strength
- Password uniqueness
- Use of outdated security protocols
- WPS configuration
- Router firmware
- Connected devices
- Network segmentation

---

## 13. Stage 10 — Security Recommendations

Based on the audit, the following recommendations can be provided:

### Strong Password

Use a long, unique and unpredictable Wi-Fi password.

### Modern Encryption

Prefer WPA3 where supported. WPA2-AES is also preferable to outdated wireless security mechanisms.

### Disable Unnecessary WPS

WPS should be disabled when it is not required.

### Firmware Updates

Keep the router firmware updated to reduce known security vulnerabilities.

### Guest Network

Use a separate guest network for untrusted devices.

### Regular Monitoring

Regularly review connected devices and router security settings.

---

## 14. Ethical Considerations

Wireless security testing must always be performed legally and responsibly.

Before testing a network, the tester should have:

1. Ownership of the network, or
2. Explicit permission from the network owner.

Testing random public, neighbor, college, office, or other private Wi-Fi networks without authorization is not part of this project.

---

## 15. Expected Learning Outcomes

After completing this project, the following concepts should be understood:

- Wireless network discovery
- SSID and BSSID
- Wireless channels
- Monitor mode
- 802.11 wireless frames
- WPA/WPA2 authentication
- Four-way handshake
- Packet capture
- Wireshark analysis
- Password security auditing
- Wireless security best practices
- Ethical penetration testing

---

## 16. Conclusion

This methodology provides a structured approach to performing a controlled Wi-Fi security audit.

The project demonstrates how wireless security tools can be used to understand wireless networks, capture and analyze authentication-related traffic, evaluate password security, and identify improvements that can strengthen a Wi-Fi network.

The entire process should be performed only in an authorized and controlled environment.