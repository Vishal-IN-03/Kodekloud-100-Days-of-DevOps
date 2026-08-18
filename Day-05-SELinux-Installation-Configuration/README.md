# 🛡️ Day 05 – Install and Configure SELinux

## 📌 Scenario

The Nautilus production support team needed to prepare an application server with **SELinux** for improved security.

The requirement was to install the necessary SELinux packages, enable SELinux, and ensure the system was configured correctly.

---

## 🎯 Objectives

* Install SELinux-related packages
* Configure SELinux on the application server
* Enable SELinux enforcement
* Verify the current SELinux status
* Ensure the configuration survives a reboot

---

## 🛠️ Tasks Performed

### ✅ 1. Check Current SELinux Status

First, checked the existing SELinux configuration:

```bash
sestatus
```

This helped determine whether SELinux was installed and what mode it was currently running in.

---

### ✅ 2. Install Required SELinux Packages

Installed the required SELinux packages using the system package manager.

```bash
sudo yum install -y selinux-policy selinux-policy-targeted
```

---

### ✅ 3. Configure SELinux

Updated the SELinux configuration:

```bash
sudo vi /etc/selinux/config
```

Configured:

```text
SELINUX=enforcing
```

The `enforcing` mode ensures that SELinux policies are actively applied.

---

### ✅ 4. Check Configuration

Verified the configured SELinux mode:

```bash
grep '^SELINUX=' /etc/selinux/config
```

Expected:

```text
SELINUX=enforcing
```

---

### ✅ 5. Verify Current Status

Checked SELinux again:

```bash
sestatus
```

Verified the SELinux status and enforcement mode.

> Depending on the initial system state, a reboot may be required for a configuration change in `/etc/selinux/config` to take effect.

---

## 🔐 Understanding SELinux Modes

SELinux has three primary modes:

### Enforcing

SELinux actively enforces security policies and blocks unauthorized actions.

### Permissive

SELinux does not block actions but logs policy violations.

### Disabled

SELinux is completely disabled.

For a production server, **Enforcing** is generally the preferred mode when the required policies are properly configured.

---

## ⚠️ Common Mistakes to Avoid

* Disabling SELinux just because an application encounters an access denial
* Changing configuration without checking the current SELinux state
* Confusing `permissive` with `enforcing`
* Forgetting that configuration changes may require a reboot
* Ignoring SELinux audit logs when troubleshooting access denials

---

## 🧠 Key Learnings

* SELinux provides an additional security layer beyond traditional Linux permissions.
* File ownership and `chmod` permissions are not the only access controls on Linux.
* SELinux uses security policies and contexts to control access.
* `sestatus` is useful for checking the current SELinux state.
* Disabling security controls should not be the first troubleshooting approach.
* Understanding **why** SELinux denies an action is more valuable than simply turning it off.

---

## 🎤 Interview Questions

### Q1. What is SELinux?

SELinux is a Linux security mechanism that provides **Mandatory Access Control (MAC)** using security policies.

### Q2. What are the three SELinux modes?

```text
Enforcing
Permissive
Disabled
```

### Q3. What is the difference between permissive and enforcing mode?

In enforcing mode, policy violations are blocked. In permissive mode, violations are logged but not blocked.

### Q4. How do you check SELinux status?

```bash
sestatus
```

### Q5. Where is the persistent SELinux configuration stored?

```text
/etc/selinux/config
```

### Q6. Why shouldn't SELinux simply be disabled when troubleshooting?

Because doing so removes an important security layer. A better approach is to investigate the denial and configure the appropriate SELinux policy or context.

---

## 📌 Final Result

```text
Linux Server
     │
     ▼
SELinux Installed
     │
     ▼
Configuration Updated
     │
     ▼
SELINUX=enforcing
     │
     ▼
Mandatory Access Control
     │
     ▼
Improved Server Security
```

🛡️ **SELinux successfully installed and configured.**

✅ **Day 05 Completed Successfully** 🚀
