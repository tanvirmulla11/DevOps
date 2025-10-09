# 🚀 DevOps Day 17: PostgreSQL Database and User Management

Today's task was a dive into the world of database administration — a critical skill for any DevOps role. The objective was to prepare a PostgreSQL database server for a new application. This wasn’t just about making sure the database was running; it was about setting up proper security and isolation for the new application's data.

I learned how to interact with PostgreSQL from the command line, create dedicated users and databases, and grant permissions. This entire process is a real-world application of the **Principle of Least Privilege** and is fundamental to building secure and maintainable systems.

---

## 📘 Table of Contents
- [The Task](#the-task)
- [My Step-by-Step Solution](#my-step-by-step-solution)
- [Why Did I Do This? (The What & Why)](#why-did-i-do-this-the-what--why)
- [Deep Dive: The Principle of Least Privilege in Databases](#deep-dive-the-principle-of-least-privilege-in-databases)
- [Common Pitfalls](#common-pitfalls)
- [Exploring the Commands Used](#exploring-the-commands-used)
- [Outcome](#outcome)

---

## 🧩 The Task

The objective was to configure the pre-installed **PostgreSQL** server on the Nautilus database server. The specific requirements were:

1. Create a new database user (role) named `kodekloud_aim`.
2. Set a specific password (`ksH85UJjhb`) for this new user.
3. Create a new, empty database named `kodekloud_db6`.
4. Grant the `kodekloud_aim` user full permissions on the `kodekloud_db6` database.

---

## ⚙️ My Step-by-Step Solution

The entire process was performed on the command line of the database server (`stdb01`).

### Step 1: Gaining Administrative Access
First, I connected to the database server and switched to the PostgreSQL administrative user.

```bash
ssh peter@stdb01
sudo -u postgres -i
psql
```
### Step 2: Executing the SQL Commands

### Inside the psql shell, I ran three SQL commands to accomplish the task.

```bash
-- Create the User
CREATE USER kodekloud_aim WITH PASSWORD 'ksH85UJjhb';

-- Create the Database
CREATE DATABASE kodekloud_db6;

-- Grant Permissions
GRANT ALL PRIVILEGES ON DATABASE kodekloud_db6 TO kodekloud_aim;
```
