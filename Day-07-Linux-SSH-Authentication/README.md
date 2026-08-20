# 👤 Day 07 – Linux User Management and Sudo Access

## 📌 Scenario

The Nautilus production support team needed to configure user access on an application server.

A user account had to be created and provided with the required administrative access while following proper Linux permission practices.

The goal was to provide the required privileges without making unnecessary changes to the system.

---

## 🎯 Objectives

* Create the required Linux user
* Configure the required administrative access
* Ensure the user can perform privileged operations
* Verify the user's sudo configuration
* Follow the principle of least privilege

---

## 🛠️ Tasks Performed

### ✅ 1. Create the User

Created the required user account on the designated application server:

```bash
sudo useradd <username>
```

---

### ✅ 2. Configure Sudo Access

Configured the user to have the required administrative privileges.

Depending on the task requirements, this can be managed through the appropriate sudo group or sudoers configuration.

For example, on systems using the `wheel` group:

```bash
sudo usermod -aG wheel <username>
```

---

### ✅ 3. Verify User Groups

Checked the user's group membership:

```bash
id <username>
```

Confirmed that the required administrative group was present.

---

### ✅ 4. Verify Sudo Configuration

Checked the effective sudo permissions:

```bash
sudo -l -U <username>
```

This verifies which commands the user is permitted to execute with elevated privileges.

---

## 🔐 Understanding Sudo Access

`sudo` allows authorized users to execute commands with elevated privileges without requiring them to log in directly as `root`.

A typical workflow is:

```text
Normal User
     │
     │ sudo command
     ▼
Privilege Check
     │
     ▼
Sudo Policy
     │
     ▼
Root-level Operation
```

This provides better accountability than sharing the root account.

---

## ⚠️ Common Mistakes to Avoid

* Giving every user unrestricted sudo access
* Editing `/etc/sudoers` incorrectly
* Forgetting to validate sudo configuration
* Using `sudo` when elevated privileges are not required
* Replacing existing group memberships instead of appending them
* Not verifying the final permissions

---

## 🧠 Key Learnings

* `sudo` provides controlled privilege escalation.
* Administrative access should be granted only when required.
* Linux groups can simplify privilege management.
* `usermod -aG` preserves existing supplementary group memberships.
* Sudo access should always be verified after configuration.
* The principle of least privilege is an important Linux security practice.

---

## 🎤 Interview Questions

### Q1. What is sudo?

`sudo` allows an authorized user to execute commands with the privileges of another user, commonly `root`.

### Q2. Why is sudo preferred over direct root login?

It provides controlled privilege escalation and improves accountability because actions can be associated with individual user accounts.

### Q3. How can you check a user's sudo permissions?

```bash
sudo -l -U <username>
```

### Q4. Why use `usermod -aG` instead of only `usermod -G`?

The `-a` option appends the user to the supplementary group instead of replacing existing supplementary group memberships.

### Q5. What is the principle of least privilege?

Users should receive only the permissions necessary to perform their required tasks.

---

## 📌 Final Result

```text
Linux Server
     │
     ▼
User Account
     │
     ▼
Required Administrative Access
     │
     ▼
Sudo Permission Verified
     │
     ▼
Controlled Privilege Escalation
```

🔐 **User access successfully configured and verified.**

✅ **Day 07 Completed Successfully** 🚀
