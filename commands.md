# Wi-Fi Security Audit — Commands

This document contains the commands used during the authorized Wi-Fi security auditing lab.

> **Disclaimer:** These commands must only be used on wireless networks that you own or have explicit permission to test.

---

## 1. Check Wireless Interface

First, identify the wireless interfaces available on the Kali Linux system.

```bash
iwconfig
```

An alternative command for identifying network interfaces is:

```bash
ip link
```

### Purpose

These commands help identify the wireless adapter and its interface name.

Example interface:

```text
wlan0
```

The actual interface name may differ depending on the system and Wi-Fi adapter.

---

## 2. Check Aircrack-ng Installation

Check whether Aircrack-ng is installed:

```bash
aircrack-ng --version
```

If the toolkit is not installed:

```bash
sudo apt update
sudo apt install aircrack-ng
```

### Purpose

Aircrack-ng provides the tools required for wireless security auditing.

---

## 3. Check Wireless Adapter

Before enabling monitor mode, check the wireless interface:

```bash
iwconfig
```

Verify that the adapter is detected correctly.

---

## 4. Enable Monitor Mode

Aircrack-ng provides `airmon-ng` for managing monitor mode.

First identify the interface:

```bash
iwconfig
```

Then enable monitor mode on the authorized lab adapter:

```bash
sudo airmon-ng start <interface>
```

Example:

```bash
sudo airmon-ng start wlan0
```

The resulting monitor-mode interface may have a name such as:

```text
wlan0mon
```

The exact name depends on the wireless adapter and driver.

---

## 5. Verify Monitor Mode

Check the interface again:

```bash
iwconfig
```

or:

```bash
ip link
```

The interface should indicate monitor mode when successfully configured.

---

## 6. Discover Wireless Networks

Use `airodump-ng` to observe wireless networks in the surrounding environment:

```bash
sudo airodump-ng <monitor-interface>
```

Example:

```bash
sudo airodump-ng wlan0mon
```

### Information Observed

The scan can display information such as:

- BSSID
- Channel
- Signal strength
- Encryption
- Authentication
- ESSID

Only the authorized laboratory network should be selected for further testing.

---

## 7. Focus on the Authorized Lab Network

Once the authorized lab access point has been identified, monitoring can be restricted to its channel and BSSID.

General format:

```bash
sudo airodump-ng --bssid <AUTHORIZED_BSSID> --channel <CHANNEL> --write wifi-audit <MONITOR_INTERFACE>
```

Example format:

```bash
sudo airodump-ng --bssid AA:BB:CC:DD:EE:FF --channel 6 --write wifi-audit wlan0mon
```

### Purpose

This focuses the capture on the authorized laboratory access point and saves the captured traffic for later analysis.

---

## 8. Capture File

The capture process may generate files such as:

```text
wifi-audit-01.cap
```

or related capture files.

These files contain captured wireless traffic.

### Important

Do not upload real private Wi-Fi captures to a public GitHub repository.

Use sanitized or synthetic lab data when publishing the project.

---

## 9. Check Captured Authentication Data

Aircrack-ng can be used to inspect a capture file:

```bash
aircrack-ng wifi-audit-01.cap
```

This can help determine whether the capture contains suitable WPA/WPA2 authentication information for an authorized security audit.

---

## 10. Password Security Testing

For an authorized laboratory network, candidate passwords can be tested against the captured authentication information.

General format:

```bash
aircrack-ng -w <WORDLIST> <CAPTURE_FILE>
```

Example:

```bash
aircrack-ng -w /path/to/wordlist.txt wifi-audit-01.cap
```

### Purpose

This evaluates whether the authorized Wi-Fi password can be matched using the selected candidate-password list.

A failed dictionary test does **not** prove that the password is impossible to crack. It only means that the tested candidate set did not produce a match.

---

## 11. Analyze Capture with Wireshark

Open the capture file using Wireshark:

```bash
wireshark wifi-audit-01.cap
```

Alternatively, open Wireshark from the Kali Linux application menu and load the capture file.

### Purpose

Wireshark can be used to examine:

- Wireless frames
- Authentication traffic
- Management frames
- Protocol information
- Packet details

---

## 12. Stop Monitor Mode

After completing the authorized security audit, stop monitor mode:

```bash
sudo airmon-ng stop <monitor-interface>
```

Example:

```bash
sudo airmon-ng stop wlan0mon
```

---

## 13. Restore Network Interface

Check the available interfaces:

```bash
iwconfig
```

If required, restart the networking service:

```bash
sudo systemctl restart NetworkManager
```

Then verify the wireless connection:

```bash
nmcli device status
```

---

## 14. Useful Verification Commands

### Check IP configuration

```bash
ip addr
```

### Check network interfaces

```bash
ip link
```

### Check wireless information

```bash
iwconfig
```

### Check NetworkManager status

```bash
nmcli device status
```

### Check Aircrack-ng version

```bash
aircrack-ng --version
```

---

## 15. Command Workflow

The overall command workflow is:

```text
Check Interface
      ↓
Check Aircrack-ng
      ↓
Enable Monitor Mode
      ↓
Verify Interface
      ↓
Discover Wireless Networks
      ↓
Select Authorized Lab Network
      ↓
Capture Authentication Traffic
      ↓
Analyze Capture
      ↓
Perform Authorized Password Audit
      ↓
Stop Monitor Mode
      ↓
Restore Network Connection
```

---

## 16. Important Notes

- Always verify the target network before performing any test.
- Only test networks that you own or have explicit permission to audit.
- Do not target neighboring or public Wi-Fi networks.
- Do not publish private Wi-Fi credentials.
- Do not upload sensitive packet captures to a public repository.
- Keep all testing within a controlled laboratory environment.