# Multi-Building LAN Setup & QuickBooks Desktop Multi-User Configuration

## 📌 Overview
This project demonstrates the design and implementation of a Local Area Network (LAN) connecting two separate buildings in a hospital environment.

The goal was to enable multi-user access to QuickBooks Desktop, along with printer sharing and attendance device integration.

---

## 🏢 Network Environment

### Building A
- Accountant PC (QuickBooks Host)
- IT Assistant PC
- Dialog Wi-Fi Router (DHCP Server)
- Unmanaged Switch

### Building B
- Account Assistant PC
- USB Printer
- Fingerprint Attendance Device
- Unmanaged Switch

---

## 🌐 Network Design

- CAT6 cable (~50 meters) used to connect both buildings
- Single subnet network: `192.168.8.0/24`
- Router acts as DHCP server

### IP Addressing

| Device | IP Address |
|--------|-----------|
| Router | 192.168.8.1 |
| Accountant PC | 192.168.8.10 |
| IT Assistant PC | 192.168.8.11 |
| Account Assistant PC | 192.168.8.20 |
| Attendance Device | 192.168.8.22 |

---

## ⚙️ Implementation Steps

### 1. Physical Setup
- Connected both buildings using CAT6 cable
- Installed unmanaged switches
- Connected all devices

### 2. QuickBooks Setup
- Installed QuickBooks Database Server Manager
- Enabled Multi-User Mode
- Shared company file
- Configured user roles

### 3. Printer Setup
- Shared USB printer over network

### 4. Attendance Device
- Assigned static IP
- Integrated with attendance software

---

## 🚨 Issue Faced

- PCs could not communicate (ping failed)
- Internet was working correctly
- Devices were in same subnet

---

## 🔧 Troubleshooting

Identified Windows Firewall blocking ICMP traffic.

### Fix:
```bash
netsh advfirewall firewall add rule name="Allow ICMPv4" protocol=icmpv4 dir=in action=allow
