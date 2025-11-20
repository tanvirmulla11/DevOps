
# Day 70 🔐 Jenkins User Access Configuration 

## 📘 Overview
The Nautilus DevOps team is integrating **Jenkins** into their CI/CD pipelines.  
After setting up a new Jenkins server, user access control must be configured using the **Project-based Matrix Authorization Strategy**.  
This ensures each user has limited, role-based permissions.

---

## 🪜 Task Steps

### 1️⃣ Access Jenkins UI
1. Click the **Jenkins** button on the top bar of the lab environment.
2. Log in with:
Username: admin
Password: Adm!n321


---

### 2️⃣ Create a New User
1. From the Jenkins dashboard, go to:


Manage Jenkins → Users → Create User

2. Fill out the form:

| Field | Value |
|--------|--------|
| Username | kareem |
| Password | YchZHRcLkL |
| Confirm Password | YchZHRcLkL |
| Full Name | Kareem |

3. Click **Create User**.

✅ The user **kareem** is now added.

---

### 3️⃣ Enable Jenkins Security and Authorization
1. Go to:


Manage Jenkins → Security → Configure Global Security

2. Under **Authentication**:
- ✅ Check **“Jenkins’ own user database”**.
- (Optional) Leave **“Allow users to sign up”** unchecked.
3. Under **Authorization**:
- Select **Project-based Matrix Authorization Strategy**.
- If this option is missing, install the plugin:
  ```
  Manage Jenkins → Plugins → Available → Matrix Authorization Strategy
  ```
  Then restart Jenkins.

---

### 4️⃣ Configure Permissions
When the matrix appears:

#### 🧑 For `admin`
- Ensure `admin` has all permissions checked (full access).

#### 👤 For `kareem`
- Click **Add user or group** → enter `kareem` → OK.
- Grant **only**:
- ✅ `Overall → Read`

#### 🚫 For `Anonymous`
- Remove or uncheck **all** permissions.

Then click **Save**.

---

### 5️⃣ Configure Project-Level Access
1. Open any existing Jenkins job.
2. Click **Configure**.
3. Scroll to **Enable project-based security**, and enable it.
4. Add user **kareem**.
5. Grant only **Job → Read** permission.
6. Click **Save**.

---

### 6️⃣ Verify Permissions
#### Test 1 — Login as Kareem
- Log out and log in with:


Username: kareem
Password: YchZHRcLkL

- Verify Kareem can **view jobs** but cannot configure or build them.

#### Test 2 — Login as Admin
- Log back in as:


Username: admin
Password: Adm!n321

- Ensure full access remains.

---

### 7️⃣ Save and Apply Changes
Once all permissions are verified:
- Click **Save** or **Apply** on the **Configure Global Security** page.

---

## ✅ Verification Checklist

| Check | Status |
|-------|--------|
| Jenkins accessible | ✅ |
| User `kareem` created | ✅ |
| Matrix Authorization enabled | ✅ |
| `kareem` has only read permission | ✅ |
| Anonymous users removed | ✅ |
| Admin retains full access | ✅ |
| Project-level read-only access configured | ✅ |

---

