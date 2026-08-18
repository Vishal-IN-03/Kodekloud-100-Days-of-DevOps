# 👤 Day 01 – Create a User with Non-Interactive Shell

## 📌 Scenario

The Nautilus production support team needed to create a new service user on an application server.

The user was required to exist for running services or automated processes, but **direct interactive login had to be prevented** for security reasons.

---

## 🎯 Objectives

* Create the required Linux user
* Configure the user with a non-interactive shell
* Prevent direct shell access
* Verify the user and assigned shell

---

## 🛠️ Tasks Performed

### ✅ 1. Connect to the Required Server

Connected to the assigned application server using the provided credentials.

---

### ✅ 2. Create the Service User

Created the required user account with a **non-interactive shell**.

The shell was configured so the account could be used by services or processes without providing normal interactive terminal access.

---

### ✅ 3. Verify User Creation

Checked the user account information:

```bash
id <username>
```

Verified that the user was successfully created.

---

### ✅ 4. Verify the Assigned Shell

Checked the user's shell configuration:

```bash
grep <username> /etc/passwd
```

Confirmed that the account was configured with a non-interactive shell.

---

## 🔐 Why a Non-Interactive Shell?

Service accounts generally do not need interactive terminal access.

Using a non-interactive shell helps:

* Reduce unnecessary login access
* Improve server security
* Prevent accidental interactive use
* Follow the principle of least privilege
* Separate service accounts from human users

---

## ⚠️ Common Mistakes to Avoid

* Creating the user with a normal interactive shell
* Giving unnecessary sudo privileges
* Forgetting to verify the assigned shell
* Creating the account on the wrong server
* Assuming user creation succeeded without validation

---

## 🧠 Key Learnings

* Linux users can be configured for specific operational purposes.
* Service accounts should have only the access they require.
* A non-interactive shell is an important security control.
* Always verify user properties after making account changes.
* Linux security is often about reducing unnecessary access rather than simply adding restrictions.

---

## 🎤 Interview Questions

### Q1. What is a service account?

A service account is a Linux user created for running applications, services, or automated processes rather than for normal human interaction.

### Q2. Why use a non-interactive shell?

It prevents the account from being used for normal interactive terminal sessions while still allowing services or processes to use the account.

### Q3. How can you check a user's assigned shell?

```bash
grep <username> /etc/passwd
```

### Q4. Why should service accounts have limited privileges?

To follow the **principle of least privilege** and reduce the impact of a compromised account.

### Q5. Is creating a user enough to verify the task?

No. The account should also be validated for its UID, groups, shell, and required permissions.

---

## 📌 Final Result

```text
Linux Server
     │
     ▼
Service User Created
     │
     ├── User account exists
     ├── Required groups configured
     └── Non-interactive shell
             │
             ▼
      Interactive login prevented
```

✅ **Day 01 Completed Successfully** 🚀
