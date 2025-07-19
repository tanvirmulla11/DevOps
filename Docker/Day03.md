# 🛠 Docker Installation Guide (All OS)

## 📦 Installing Docker Engine

### 🐧 Ubuntu (Debian-based)

```bash
# 1. Update the package index and install dependencies
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# 2. Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
    sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# 3. Set up the Docker repository
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 4. Install Docker Engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 5. Verify Docker installation
docker --version

# 6. Run your first Docker container
sudo docker run hello-world

# 🪟 Installing Docker on Windows

> ✅ **System Requirements**  
- Windows 10 64-bit: Pro, Enterprise, or Education  
- Build 15063 or later  
- Hyper-V and WSL 2 support enabled
```

## 📥 Step-by-Step Installation

1. **Download Docker Desktop**  
   👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

2. **Run the installer**  
   Follow the on-screen instructions.

3. **Enable WSL 2 feature**  
   Docker Desktop will prompt you to enable WSL 2 and install required components.

4. **Restart your system**  
   A restart may be required after installation.

---

## 🧪 Verify Installation

Open **Command Prompt** or **PowerShell** and run:

```powershell
docker --version
docker run hello-world
```
If installed correctly, you will see:
Hello from Docker!
This message shows that your installation appears to be working correctly.

# 🍏 Installing Docker on macOS

> ✅ **System Requirements**  
- macOS 10.15+ (Catalina or newer)

---

## 📥 Step-by-Step Installation

1. **Download Docker Desktop for Mac**  
   👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

2. **Install Docker Desktop**  
   - Open the `.dmg` file  
   - Drag **Docker** into the **Applications** folder

3. **Launch Docker**  
   - Go to **Applications**
   - Open **Docker**
   - Wait for Docker to initialize (whale icon in the menu bar)

---

## 🧪 Verify Installation

Open **Terminal** and run the following:

```bash
docker --version
docker run hello-world
```

---

## ✅ Expected Output

If **installed** correctly, you will see:

```bash
Hello from Docker!
This message shows that your installation appears to be working correctly.
```
---
---

## 🚀 You're All Set!

You've successfully installed Docker and run your first container using `hello-world`! 🎉  
Now you're ready to:

- Build and manage containerized applications
- Explore Dockerfiles and custom images
- Work with volumes, networks, and orchestration tools like Docker Compose

Keep experimenting and building — the container world is yours to explore! 🌍🐳

---

## 🙌 Contributing

Found a typo, bug, or want to improve this guide?  
Feel free to open an issue or submit a pull request!

---

## 📬 Stay Connected

If you found this helpful, consider giving the repo a ⭐ and following for more DevOps and cloud content.

Happy Dockering! ⚙️🐳





