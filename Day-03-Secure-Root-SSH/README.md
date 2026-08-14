# 🔐 Day 03 – Disable Direct Root SSH Login

## 📌 Scenario

The Nautilus production support team needed to improve the security of an application server.

Direct SSH access for the **root user** was considered a security risk. The requirement was to disable direct root login through SSH while ensuring that normal authorized users could still connect to the server.

---

## 🎯 Objectives

* Configure SSH to prevent direct root login
* Modify the SSH server configuration safely
* Validate the configuration before restarting the service
* Restart SSH and verify the security change

---

## 🛠️ Tasks Performed

### ✅ 1. Check Current SSH Configuration

Reviewed the SSH server configuration to understand the existing root-login setting.

```bash
sudo vi /etc/ssh/sshd_config
```

Located the relevant directive:

```text
PermitRootLogin
```

---

### ✅ 2. Disable Direct Root Login

Configured SSH to prevent direct root authentication:

```text
PermitRootLogin no
```

This prevents users from logging directly into the server through SSH as `root`.

---

### ✅ 3. Validate SSH Configuration

Before restarting the service, validated the configuration:

```bash
sudo sshd -t
```

A successful validation produced no configuration errors.

> Always validate SSH configuration before restarting the service. A syntax mistake can prevent SSH from starting and potentially lock administrators out.

---

### ✅ 4. Restart SSH Service

After successful validation, restarted the SSH service:

```bash
sudo systemctl restart sshd
```

---

### ✅ 5. Verify SSH Service

Checked the service status:

```bash
sudo systemctl status sshd
```

Confirmed that the SSH service was running successfully.

---

## 🔍 Verification

Checked the effective SSH configuration:

```bash
sudo sshd -T | grep permitrootlogin
```

Expected:

```text
permitrootlogin no
```

This confirmed that direct root SSH login was disabled.

---

## ⚠️ Common Mistakes to Avoid

* Editing the wrong SSH configuration file
* Forgetting to validate `sshd_config`
* Restarting SSH without testing the configuration
* Accidentally locking out the only administrative user
* Disabling SSH access without confirming another authorized user can log in
* Assuming a configuration change is active without verification

---

## 🧠 Key Learnings

* Direct root SSH access increases security risk.
* SSH configuration changes should always be validated before restarting the service.
* `sshd -t` is useful for detecting configuration syntax errors.
* `sshd -T` can be used to inspect the effective SSH configuration.
* Security changes should always be verified after implementation.
* In production environments, maintaining an existing administrative session while changing SSH configuration is a good safety practice.

---

## 🎤 Interview Questions

### Q1. Why disable direct root SSH login?

It reduces the risk of unauthorized privileged access and makes administrators authenticate through controlled user accounts.

### Q2. Which file controls the OpenSSH server configuration?

```text
/etc/ssh/sshd_config
```

### Q3. How do you validate the SSH configuration?

```bash
sudo sshd -t
```

### Q4. What does `PermitRootLogin no` do?

It prevents direct SSH login as the `root` user.

### Q5. Why should SSH configuration be validated before restarting?

A configuration error could stop the SSH service from restarting and potentially make remote access unavailable.

---

## 📌 Final Result

```text
SSH Client
    │
    │ SSH Login
    ▼
SSH Server
    │
    ├── Regular authorized user → ✅ Allowed
    │
    └── root user → ❌ Direct login blocked
```

🔐 **Direct root SSH login successfully disabled.**

✅ **Day 03 Completed Successfully** 🚀
