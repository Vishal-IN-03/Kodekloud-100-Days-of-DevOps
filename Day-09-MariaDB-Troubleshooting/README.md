# 🗄️ Day 09 – MariaDB Troubleshooting

## 📌 Scenario

The Nautilus DevOps team is experiencing an issue with the **MariaDB database service** on one of the application servers.

The database service needs to be investigated, the underlying issue identified, and MariaDB restored to a working state without affecting the existing database configuration or data.

---

## 🎯 Objectives

* Check the current MariaDB service status.
* Investigate why the database service is not working correctly.
* Inspect service logs and configuration.
* Fix the underlying issue.
* Restart MariaDB successfully.
* Verify that the database service is operational.

---

## 🛠️ Tasks Performed

### 1. Check MariaDB Service Status

First, checked the current status of the MariaDB service:

```bash
sudo systemctl status mariadb
```

This helps determine whether the service is running, stopped, or failing.

---

### 2. Investigate the Failure

Instead of immediately restarting the service, investigated the error reported by `systemctl`.

Checked MariaDB logs:

```bash
sudo journalctl -u mariadb
```

The logs were used to identify the actual cause of the service failure.

---

### 3. Check MariaDB Configuration

Inspected the relevant MariaDB configuration files to identify any configuration-related problems.

Typical configuration locations include:

```text
/etc/my.cnf
/etc/my.cnf.d/
```

The configuration was checked carefully before making any changes.

---

### 4. Fix the Identified Issue

After identifying the problem, corrected the faulty configuration/environment responsible for the MariaDB failure.

The existing database data and required configuration were preserved.

---

### 5. Restart MariaDB

Once the issue was fixed, restarted the database service:

```bash
sudo systemctl restart mariadb
```

---

### 6. Verify Service Status

Confirmed that MariaDB was running successfully:

```bash
sudo systemctl status mariadb
```

The expected result was:

```text
Active: active (running)
```

---

## 🔍 Verification

Performed the following checks:

```bash
sudo systemctl is-active mariadb
```

Expected:

```text
active
```

Also verified that MariaDB was responding correctly after the troubleshooting process.

---

## 🚨 Problems / Troubleshooting Approach

One of the most important lessons from this task was **not to blindly restart a failed service**.

A better troubleshooting sequence is:

```text
Service Status
      ↓
Check Logs
      ↓
Identify Root Cause
      ↓
Fix the Problem
      ↓
Restart Service
      ↓
Verify
```

This approach is much more useful in real production environments than repeatedly running:

```bash
sudo systemctl restart mariadb
```

without understanding why it failed.

---

## 🧠 Key Learnings

* `systemctl status` is one of the first commands to use when troubleshooting Linux services.
* `journalctl -u <service>` provides valuable service-specific logs.
* Service failures can be caused by configuration errors, permissions, ports, missing files, or dependencies.
* Restarting a service without checking logs can hide the actual root cause.
* Database troubleshooting requires extra caution because existing data must not be damaged.
* A service being installed does not necessarily mean it is running correctly.

---

## 🎤 Interview Questions

### 1. How do you check whether MariaDB is running?

```bash
sudo systemctl status mariadb
```

### 2. How do you check MariaDB logs?

```bash
sudo journalctl -u mariadb
```

### 3. What is the difference between `systemctl restart` and `systemctl start`?

`start` starts a service that is not running, while `restart` stops and starts the service again.

### 4. Why should you check logs before restarting a failed service?

Logs often contain the actual error and root cause. Restarting without investigating can make troubleshooting slower and may not fix the underlying problem.

### 5. How can you check whether a service is currently active?

```bash
sudo systemctl is-active mariadb
```

---

## 📌 Final Result

✅ MariaDB issue investigated
✅ Service logs checked
✅ Root cause identified
✅ Required correction applied
✅ MariaDB restarted successfully
✅ Database service verified as operational

**Day 09 completed — MariaDB troubleshooting successfully performed. 🚀**
