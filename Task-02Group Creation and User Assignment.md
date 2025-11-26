

# **Day-01 — Linux System Administration(Task-02)

Group & User Management 

Today’s task focused on applying Linux user-group administration across multiple servers in a distributed environment.

---

## 🧩 **Task Summary**

The objective was to streamline access control across all **App Servers** in the *Stratos Datacenter*.

### ✔ Requirements:

1. **Create a group** named `nautilus_noc` on all App servers.
2. **Add user `mohammed`** to this group.
3. **If the user doesn’t exist, create it.**

The work had to be performed on **three App servers**.

---

## 🖥️ **Steps Performed**

### **1️⃣ SSH into each App Server**

From the jump host:

```bash
ssh tony@stapp01
```

(Use the credentials provided in the *Details of all Users and Servers* panel.)

Repeat this for:

```
stapp01
stapp02
stapp03
```

---

## **2️⃣ Create the group `nautilus_noc`**

On every App server:

```bash
sudo groupadd nautilus_noc
```

> If the group already exists, the system will show an error — safe to ignore.

---

## **3️⃣ Check if the user mohammed exists**

```bash
id mohammed
```

If it shows **no such user**, create it:

```bash
sudo useradd mohammed
```

---

## **4️⃣ Add the user to the group**

```bash
sudo usermod -aG nautilus_noc mohammed
```

---

## **5️⃣ Verify**

```bash
id mohammed
```

Expected:
`nautilus_noc` should appear in the list of groups.

---

## **6️⃣ Repeat the same steps for all App servers**

* stapp01
* stapp02
* stapp03

After completing all three, return to the lab UI and click **Check**.

---

## 💡 **Key Learnings**

* How to access distributed servers and use SSH navigation properly
* Creating groups for centralized access control
* Adding users to secondary groups using `usermod -aG`
* Validating users and permissions using `id`
* Understanding multi-server configuration consistency in a production-like environment

---

## ✅ **Final Command Set (Quick Copy-Paste)**

Run these on *each* App server:

```bash
sudo groupadd nautilus_noc 2>/dev/null
id mohammed || sudo useradd mohammed
sudo usermod -aG nautilus_noc mohammed
```

---


