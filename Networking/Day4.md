# 🌐 IP Address Classes & Address Resolution Protocols (ARP / RARP)

This document provides a **clear and professional explanation** of **IP address classes** and **Address Resolution Protocols**, suitable for **academic use**, **GitHub repositories**, or **interview preparation**.

---

## 📌 IP Address Classes

IPv4 addresses are divided into **five different classes** based on their structure and intended usage.

### 🔹 Class A
- **Starting Bit Pattern:** `0`
- **Network ID:** 1 byte  
- **Host ID:** 3 bytes  
- **Host Capacity:** Very large (supports millions of hosts)
- **Usage:** Large organizations and networks

---
### 🔹 Class B
- **Starting Bit Pattern:** `10`
- **Network ID:** 2 bytes  
- **Host ID:** 2 bytes  
- **Host Capacity:** Medium-sized networks
- **Usage:** Universities, large enterprises

---
### 🔹 Class C
- **Starting Bit Pattern:** `110`
- **Network ID:** 3 bytes  
- **Host ID:** 1 byte  
- **Host Capacity:** Small networks
- **Usage:** Small organizations, LANs

---
### 🔹 Class D
- **Starting Bit Pattern:** `1110`
- **Purpose:** Multicast addressing
- **Usage:** Video streaming, online conferencing, group communication

---
### 🔹 Class E
- **Starting Bit Pattern:** `1111`
- **Purpose:** Reserved for experimental and future use
- **Usage:** Research and testing only

---
## 🔄 Address Resolution Protocol (ARP)

### 📘 What is ARP?
**Address Resolution Protocol (ARP)** is used to map an **IP address** to a **physical (MAC) address** on a local network.

### 🔧 How ARP Works
1. A host wants to communicate with another device on the same network.
2. It broadcasts an **ARP request** containing the destination IP address.
3. All devices receive the request, but only the target device responds.
4. The target sends back its **MAC address**.
5. The sender stores this mapping in its **ARP cache**.
6. Data transmission continues using the physical address.

### 🧠 Key Points
- Works within a **Local Area Network (LAN)**
- Reduces network overhead using **cache memory**
- Essential for successful packet delivery

---
## 🔁 Reverse Address Resolution Protocol (RARP)

### 📘 What is RARP?
**RARP** allows a device to discover its **IP address** when it only knows its **physical (MAC) address**.

### ❓ Why Do We Need RARP?
Some devices (like diskless workstations):
- Do not have a hard disk
- Cannot store an IP address locally
- Need to request their IP from a network server

### 🔧 How RARP Works
1. The host broadcasts an **RARP request** with its MAC address.
2. A **RARP server** on the network recognizes the request.
3. The server responds with the corresponding IP address.
4. The host configures itself using the received IP.

### ⚠️ Note
- RARP has mostly been replaced by **BOOTP** and **DHCP**
- Still important for understanding network fundamentals

---

## ✅ Summary

| Topic | Purpose |
|-----|--------|
| IP Classes | Define network size and usage |
| ARP | Maps IP address → MAC address |
| RARP | Maps MAC address → IP address |

---
