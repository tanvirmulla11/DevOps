
# 🔐 DevOps Day 13: Securing Servers with iptables Firewall

This project demonstrates how to secure application servers using `iptables`, one of the most widely used Linux firewalls. The task was focused on protecting Apache servers running on port `8086` by allowing only trusted traffic from the Load Balancer (LBR) host, while rejecting all other connections.

---

## 📑 Table of Contents
- [Overview](#overview)
- [The Task](#the-task)
- [Step-by-Step Solution](#step-by-step-solution)
- [Deep Dive: Why Rule Order Matters](#deep-dive-why-rule-order-matters)
- [Common Pitfalls](#common-pitfalls)
- [Commands Used](#commands-used)
- [Verification](#verification)
- [Key Takeaways](#key-takeaways)

---

## 📌 Overview
In modern DevOps workflows, securing infrastructure is as critical as deploying applications. This exercise focuses on firewall security by leveraging `iptables` to enforce strict access rules for application servers in the **Nautilus Stratos DC Lab Environment**.

---

## 🎯 The Task
1. Install and configure `iptables` on all **three app servers** (`stapp01`, `stapp02`, `stapp03`).
2. Block all **incoming traffic to port 8086**, except from the **Load Balancer (LBR)** host.
3. Ensure firewall rules are **persistent across reboots**.

---

## 🛠️ Step-by-Step Solution

### Prerequisite: Identify the LBR IP
- Found the trusted IP for **stlb01** (e.g., `172.16.238.14`).

### Main Workflow (repeat on each app server)
1. **Install iptables services**
   ```bash
   sudo yum install -y iptables-services
   ```
2. **Start and enable iptables**
   ```bash
   sudo systemctl start iptables
   sudo systemctl enable iptables
   ```
3. **Add firewall rules in correct order**
   ```bash
   sudo iptables -I INPUT 1 -s 172.16.238.14 -p tcp --dport 8086 -j ACCEPT
   sudo iptables -A INPUT -p tcp --dport 8086 -j REJECT
   ```
4. **Save rules for persistence**
   ```bash
   sudo service iptables save
   ```
## 🔍 Deep Dive: Why Rule Order Matters

### iptables processes rules in order.

### By inserting the ACCEPT rule first, trusted traffic from the LBR is allowed before any blocking happens.

### If the REJECT rule came first, it would block everything — even trusted sources.\
---
## ⚠️ Common Pitfalls# Install iptables
sudo yum install -y iptables-services

# Start & enable firewall
sudo systemctl start iptables
sudo systemctl enable iptables

# Allow traffic from LBR host
sudo iptables -I INPUT 1 -s 172.16.238.14 -p tcp --dport 8086 -j ACCEPT

# Block all other traffic to port 8086
sudo iptables -A INPUT -p tcp --dport 8086 -j REJECT

# Save firewall rules
sudo service iptables save

# Verify rules
sudo iptables -L INPUT -n --line-numbers
---
## ✅ Verification

### From LBR host, accessing port 8086 → ✅ Allowed.

### From any other host, accessing port 8086 → ❌ Rejected.
---

## 📝 Key Takeaways

### Firewalls are first line of defense in server security.

### Rule order in iptables is critical for correct functionality.

### Always make rules persistent to survive reboots.

### Security should be built into DevOps workflows, not an afterthought.

## Images
<img width="1919" height="969" alt="Screenshot 2025-10-02 061147" src="https://github.com/user-attachments/assets/000c6bf0-f74c-4f8a-96ea-58b9b412aa99" />
<img width="1919" height="968" alt="Screenshot 2025-10-02 061124" src="https://github.com/user-attachments/assets/99bd3c52-3849-473d-b7b8-130de3fc4a3a" />

   
