

# 🧩 Day 72: Jenkins Parameterized Builds

## 📘 Objective
Create a simple **parameterized Jenkins job** that takes user input and echoes the values.

---

## ⚙️ Steps

### 1️⃣ Access Jenkins
- Click the **Jenkins** button on the top bar.  
- Login with:
Username: admin
Password: Adm!n321

---

### 2️⃣ Create a New Job
1. Click **New Item**.  
2. Enter name: `parameterized-job`.  
3. Select **Freestyle project** → Click **OK**.

---

### 3️⃣ Add Parameters
1. Check **This project is parameterized**.  
2. Click **Add Parameter → String Parameter**  
 - **Name:** `Stage`  
 - **Default Value:** `Build`  
3. Click **Add Parameter → Choice Parameter**  
 - **Name:** `env`  
 - **Choices:**  
   ```
   Development
   Staging
   Production
   ```

---

### 4️⃣ Configure Build
1. Scroll to **Build → Execute Shell**.  
2. Add this script:
 ```bash
 echo "Stage: ${Stage}"
 echo "Environment: ${env}"
```

## 5️⃣ Save and Build


```bash
Click Save.
On the left panel, click Build with Parameters.
```
```bash
Choose:
Stage: (default: Build)
env: Production
```
```bash
Click Build.
```

## 6️⃣ Verify


Open the build → Console Output.

```bash
You should see:
Stage: Build
Environment: Production
```



## ✅ Result
You have successfully:


Created parameterized-job


Added string and choice parameters


Executed a shell script using parameters


Verified output for Production environment

