# 🔐 Day 04 – Linux Script Execution Permissions

## 📌 Scenario

The Nautilus production support team had a shell script on **App Server 3**:

```text
/tmp/xfusioncorp.sh
```

The script needed to be executable by **all users** on the server.

The challenge was to modify the file permissions correctly without changing the script itself.

---

## 🎯 Objectives

* Locate the existing shell script
* Grant execution permission to all users
* Ensure the script is also readable by all users
* Verify the final permissions
* Confirm that the script can be executed successfully

---

## 🛠️ Tasks Performed

### ✅ 1. Check Existing Permissions

First, inspected the script's current permissions:

```bash
ls -l /tmp/xfusioncorp.sh
```

This helped identify which permissions were missing.

---

### ✅ 2. Update Script Permissions

Granted read and execute permissions to the owner, group, and other users:

```bash
sudo chmod a+rx /tmp/xfusioncorp.sh
```

Here:

* `a` → all users
* `r` → read permission
* `x` → execute permission

---

### ✅ 3. Verify Permissions

Checked the file again:

```bash
ls -l /tmp/xfusioncorp.sh
```

Expected permission structure:

```text
-rwxr-xr-x
```

This means:

```text
Owner  → read + write + execute
Group  → read + execute
Others → read + execute
```

---

### ✅ 4. Execute the Script

Tested the script:

```bash
/tmp/xfusioncorp.sh
```

The script executed successfully.

---

## 🚨 Problem / Important Detail

Initially, it may seem that only `x` permission is required to execute a shell script.

However, a script also needs to be **readable** so the shell can read its contents before executing the commands.

Therefore:

```bash
chmod a+x
```

may not be sufficient when the script is not already readable.

The safer permission change for this task was:

```bash
sudo chmod a+rx /tmp/xfusioncorp.sh
```

This ensures all users can both **read and execute** the script.

---

## ⚠️ Common Mistakes to Avoid

* Giving only execute permission when read permission is also required
* Using `chmod 777` unnecessarily
* Modifying the script contents instead of its permissions
* Forgetting to verify permissions with `ls -l`
* Testing the script without checking whether the correct file was modified

---

## 🧠 Key Learnings

* Linux permissions control who can read, modify, and execute files.
* `r`, `w`, and `x` represent read, write, and execute permissions.
* Permissions are applied separately to **owner, group, and others**.
* A shell script generally needs read permission in addition to execute permission.
* `chmod` should be used carefully because excessive permissions can create security risks.
* Always verify permission changes after modifying them.

---

## 🎤 Interview Questions

### Q1. What does `chmod a+rx` mean?

It adds **read and execute permissions** for all users.

### Q2. What does `755` represent?

```text
rwxr-xr-x
```

* Owner → `rwx`
* Group → `r-x`
* Others → `r-x`

### Q3. Why shouldn't we use `chmod 777` unnecessarily?

It gives everyone read, write, and execute access, which can introduce serious security risks.

### Q4. How do you check Linux file permissions?

```bash
ls -l <file>
```

### Q5. What are the three basic Linux file permissions?

```text
r → Read
w → Write
x → Execute
```

---

## 📌 Final Result

```text
/tmp/xfusioncorp.sh
        │
        ▼
   Permissions Updated
        │
        ▼
    rwxr-xr-x
        │
        ├── Owner  → Read + Write + Execute
        ├── Group  → Read + Execute
        └── Others → Read + Execute
        │
        ▼
   Script Executed Successfully
```

🔐 **Script execution permissions successfully configured.**

✅ **Day 04 Completed Successfully** 🚀
