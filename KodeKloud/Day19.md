# 🚀 DevOps Day 19: Hosting Multiple Websites on a Single Apache Server

---

## 🧩 Overview
Today's task was a very common web administration scenario: **hosting two separate websites on a single server**.  
This required me to install and configure the Apache web server, transfer website files from another machine, and set them up to be accessible under different URL paths.

This was a great practical exercise combining **multi-server operations** with **core Apache configuration concepts**.  
I learned how Apache’s document root and subdirectory structure work together to serve different content based on the requested URL — a simple and efficient way to manage multiple small sites without virtual hosts.

---

## 🗂️ Table of Contents
- [The Task](#-the-task)
- [My Step-by-Step Solution](#️-my-step-by-step-solution)
- [Why Did I Do This?](#-why-did-i-do-this)
- [Deep Dive: How Apache Maps URLs to Directories](#-deep-dive-how-apache-maps-urls-to-directories)
- [Common Pitfalls](#️-common-pitfalls)
- [Exploring the Commands Used](#-exploring-the-commands-used)

---

## 🎯 The Task
My objective was to set up a web server on **App Server 1** to host two static websites.

**Requirements:**
- Install the Apache (`httpd`) web server.
- Configure Apache to listen on **port 6400**.
- Website content located on the **jump host**:
  - `/home/thor/ecommerce`
  - `/home/thor/games`
- Make them accessible at:
  - `http://localhost:6400/ecommerce/`
  - `http://localhost:6400/games/`

---

## ⚙️ My Step-by-Step Solution

### 🔹 Phase 1: Preparing the Web Server (on App Server 1)
```bash
# Connect to App Server 1
ssh tony@stapp01

# Install Apache
sudo yum install -y httpd

# Edit Apache configuration file
sudo vi /etc/httpd/conf/httpd.conf
# Change the port from 80 to 6400
# Listen 6400

# Start and enable Apache
sudo systemctl start httpd
sudo systemctl enable httpd

