# Jenkins Job Permissions – KodeKloud Lab Solution

## 🎯 Task Summary
Grant specific job-level permissions to existing Jenkins users **sam** and **rohan** for the job **Packages** using **Project-Based Matrix Authorization** with **Inherit permissions from parent ACL** enabled.

---

# 🔐 1. Login to Jenkins

Use the credentials provided in the lab:

- **Username:** `admin`  
- **Password:** `Adm!n321`

---

# 🔌 2. Install Required Plugin

The lab requires the plugin:

### ✅ Project-based Matrix Authorization Strategy

### Steps:
1. Go to **Manage Jenkins → Manage Plugins**
2. Open the **Available** tab
3. Search for:
Project-based Matrix Authorization Strategy

yaml
Copy code
4. Tick the checkbox beside the plugin
5. Click **Install without restart**
6. After installation, select:
**Restart Jenkins when installation is complete and no jobs are running**

If Jenkins UI becomes unresponsive, refresh manually.

---

# 📦 3. Open the `Packages` Job

1. From the Jenkins Dashboard  
2. Click **Packages**
3. Click **Configure** (left side panel)

---

# 🔒 4. Enable Project-Based Security

Inside the job configuration page:

### Enable:
☑ Enable project-based security

shell
Copy code

### Select Inheritance Strategy:
☑ Inherit permissions from parent ACL

yaml
Copy code

This enables fine-grained permissions inside this job.

---

# 👤 5. Configure Permissions for User: sam

Add a new user entry with username: `sam`

### Grant ONLY the following permissions:

| Permission | Status |
|-----------|--------|
| Read      | ✔ |
| Build     | ✔ |
| Configure | ✔ |

Representation:
sam:

Read

Build

Configure

yaml
Copy code

---

# 👤 6. Configure Permissions for User: rohan

Add a new user entry with username: `rohan`

### Grant these permissions:

| Permission | Status |
|-----------|--------|
| Read      | ✔ |
| Build     | ✔ |
| Cancel    | ✔ |
| Configure | ✔ |
| Update    | ✔ |
| Tag       | ✔ |

Representation:
rohan:

Read

Build

Cancel

Configure

Update

Tag

yaml
Copy code

---

# 💾 7. Save the Job

Scroll to the bottom and click:

Save

yaml
Copy code

This saves the security configuration for the **Packages** job.

---

# 📸 Recommended Screenshots for KodeKloud Review

Capture these screenshots to ensure the task passes:

1. **Installed Plugin**
   - Manage Jenkins → Manage Plugins → Installed  
   - Show: *Project-based Matrix Authorization Strategy*

2. **Job Security Settings**
   - Packages → Configure  
   - Checkbox: Enable project-based security  
   - Checkbox: Inherit permissions from parent ACL  

3. **Permissions Matrix**
   - Show correct entries for:
     - `sam`
     - `rohan`

---

# ✅ Final Status
Your Jenkins job permissions for the **Packages** job have been configured successfully.  
This solution will pass the KodeKloud lab without any issues.

