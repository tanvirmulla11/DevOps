<<<<<<< HEAD
# 🔗 URL Shortener using Flask

This is a simple **URL Shortener Web App** built using Python's Flask framework.  
It takes a long URL and generates a short version that redirects to the original link.

---

## 📂 Key Deployment Steps

1. **Launch EC2 instance** (Ubuntu 22.04)  
2. **SSH into EC2** using key pair  
3. **Update & install packages** (Python, pip, virtualenv, Git)  
4. **Clone the Django repo**  
5. **Setup virtual environment**  
6. **Configure `settings.py` for allowed hosts & static files**  
7. **Run migrations and collect static files**  
8. **Test server with Gunicorn**  
9. **Install & configure Nginx as reverse proxy**  
10. **Set up domain & firewall rules (optional)**

---

## 🎯 What This Project Does

- ✅ Accepts a long URL from the user
- 🔁 Generates a unique short code
- 📥 Stores the mapping in a database (SQLite)
- 🌐 Redirects users when they visit the short URL

---


## 🔧 Project Overview

- 🖥️ **Framework**: Django (Python-based)
- ☁️ **Cloud Platform**: AWS EC2 (Ubuntu 22.04)
- 🌐 **Web Server**: Gunicorn + Nginx
- 🐘 **Database**: SQLite (can be replaced with PostgreSQL/MySQL)
- 🔒 **Security**: Configured UFW firewall, SSH key-based access

---

## 🛠 Tech Stack

- **Backend**: Python, Flask  
- **Frontend**: HTML, CSS, Bootstrap  
- **Database**: SQLite  
- **Templating**: Jinja2  

---

## 💻 How to Run the Project


1.Clone the Repository
git clone "CHOOSE YOUR WISHED FILE"
cd URL_Shortner

2.Install Required Packages
pip install -r requirements.txt

3.Run the Flask App
python app.py

---


## 🎥 Video Walkthrough

Here’s a full step-by-step video showing how I deployed the Django app to EC2:

👉 **[Watch the Hosting Video](https://www.linkedin.com/posts/tanvir-mulla-198309251_aws-django-ec2-activity-7344208813438263296-FiSH?utm_source=share&utm_medium=member_desktop&rcm=ACoAAD4o8cQBoxlOyxzep3NPl2yi2a-A18LwdVs)**  
> 

---

## 🔗 Connect with Me

- 🔗 [LinkedIn](https://www.linkedin.com/in/tanvir-mulla-198309251/)
- 🐙 [GitHub](https://github.com/tanvirmulla11)

---


Thanks for checking out this project!  
Feel free to ⭐ star the repo or connect if you’re also exploring **cloud + backend deployment**.




=======
# 🔗 URL Shortener using Flask

This is a simple **URL Shortener Web App** built using Python's Flask framework.  
It takes a long URL and generates a short version that redirects to the original link.

---

## 🎯 What This Project Does

- ✅ Accepts a long URL from the user
- 🔁 Generates a unique short code
- 📥 Stores the mapping in a database (SQLite)
- 🌐 Redirects users when they visit the short URL

---

## 🛠 Tech Stack

- **Backend**: Python, Flask  
- **Frontend**: HTML, CSS, Bootstrap  
- **Database**: SQLite  
- **Templating**: Jinja2  

---

## 🗂 Project Structure
---
URL_Shortner/
│
├── app.py # Main Flask app (routes, logic)
├── requirements.txt # Required Python packages
│
└── templates/ # HTML Templates
├── base.html # Common layout for all pages
├── index.html # Input form to paste long URL
└── result.html # Displays generated short URL
---
>>>>>>> e385147 (initial commit)
