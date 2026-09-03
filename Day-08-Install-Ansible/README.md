# ⚙️ Day 08 – Install Ansible

## 📌 Scenario

The Nautilus DevOps team wants to start using **Ansible** for configuration management and automation.

The requirement is to install **Ansible version 4.9.0** on the **Jump Host** and make sure the Ansible command is available globally so that users on the system can execute it.

---

## 🎯 Objectives

* Install `pip3` if required.
* Install **Ansible 4.9.0** on the Jump Host.
* Make Ansible available system-wide.
* Verify that the correct Ansible version is installed.

---

## 🛠️ Tasks Performed

### 1. Install Python 3 pip

Installed `python3-pip` on the Jump Host so Ansible could be installed using Python's package manager.

```bash
sudo yum install python3-pip -y
```

---

### 2. Install Ansible 4.9.0

Installed the required Ansible version globally using `pip3`.

```bash
sudo pip3 install ansible==4.9.0
```

The `sudo` option ensures the package is installed system-wide rather than only for the current user.

---

### 3. Verify Ansible Installation

Checked the installed Ansible version:

```bash
ansible --version
```

The output should show:

```text
ansible [core ...]
```

and indicate the Ansible 4.9.0 installation.

---

## 🔍 Verification

Confirmed that:

* Python `pip3` is installed.
* Ansible is installed on the Jump Host.
* The required Ansible version is installed.
* The `ansible` command is available globally.

Example:

```bash
which ansible
```

and:

```bash
ansible --version
```

---

## 🧠 Key Learnings

* **Ansible** is an automation and configuration-management tool.
* Ansible can be installed through Python's package manager, `pip3`.
* Installing packages with `sudo` can make them available system-wide.
* Version-specific installations are important when a task requires a particular release.
* Always verify software installation using its version command rather than assuming the installation succeeded.

---

## 🎤 Interview Questions

### 1. What is Ansible?

Ansible is an open-source automation tool used for configuration management, application deployment, and infrastructure automation.

### 2. Is Ansible agent-based?

No. Ansible is generally **agentless**. It connects to managed Linux systems primarily through SSH.

### 3. What is `pip3`?

`pip3` is Python 3's package manager. It is used to install Python packages and applications distributed through Python's package ecosystem.

### 4. Why would you install a specific Ansible version?

A specific version may be required for compatibility, stability, or because an organization's automation environment depends on that version.

### 5. What is the Jump Host?

A Jump Host, also called a bastion host, is a controlled server used as an entry point to access other servers in an infrastructure environment.

---

## 📌 Final Result

✅ Python `pip3` installed
✅ Ansible 4.9.0 installed
✅ Ansible available system-wide
✅ Installation verified successfully

**Day 08 completed — Ansible installation and verification successfully performed. 🚀**
