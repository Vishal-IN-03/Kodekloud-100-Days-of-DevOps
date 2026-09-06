# ☕ Day 11 – Install and Configure Tomcat

## 📌 Scenario

The Nautilus DevOps team wants to deploy a Java-based application on one of the application servers.

For this task, **Apache Tomcat** needs to be installed and configured so that it can serve applications on the required port.

---

## 🎯 Objectives

* Install Java if required.
* Download and install Apache Tomcat.
* Configure Tomcat on the application server.
* Start the Tomcat service.
* Enable Tomcat to start automatically when the server boots.
* Verify that Tomcat is running correctly.

---

## 🛠️ Tasks Performed

### 1. Check Java Installation

Since Tomcat is a Java-based application server, first verified whether Java was available:

```bash
java -version
```

If Java was not installed, the required Java package was installed.

---

### 2. Install Apache Tomcat

Downloaded and installed the required Tomcat version on the application server.

The Tomcat installation was placed in the appropriate application directory.

---

### 3. Configure Tomcat

Configured the Tomcat installation according to the task requirements.

Important Tomcat configuration files are located under:

```text
conf/
```

For example:

```text
server.xml
```

The `server.xml` file contains important server and connector configuration.

---

### 4. Start Tomcat

Started the Tomcat service/application after completing the configuration.

```bash
sudo systemctl start tomcat
```

---

### 5. Enable Tomcat at Boot

Configured Tomcat to start automatically after a system reboot:

```bash
sudo systemctl enable tomcat
```

---

## 🔍 Verification

Checked the Tomcat service status:

```bash
sudo systemctl status tomcat
```

Expected:

```text
Active: active (running)
```

Also verified that Tomcat was listening on the required port:

```bash
sudo ss -lntp
```

The configured Tomcat port should appear in the output.

---

## 🚨 Problems / Troubleshooting

When working with Tomcat, common problems include:

* Java not being installed.
* Incorrect Java environment configuration.
* Incorrect Tomcat configuration.
* Port already being used by another service.
* Incorrect file ownership or permissions.
* Tomcat failing to start because of a configuration error.

A useful troubleshooting approach is:

```text
Check Service Status
        ↓
Check Tomcat Logs
        ↓
Check Configuration
        ↓
Check Port
        ↓
Fix the Root Cause
        ↓
Restart Tomcat
        ↓
Verify
```

Tomcat logs can be particularly useful when the service starts and then immediately stops.

---

## 🧠 Key Learnings

* Tomcat is a Java-based web/application server.
* Java must be available for Tomcat to run.
* `server.xml` is an important Tomcat configuration file.
* Services should be verified after installation rather than assuming they are running.
* Port conflicts are a common cause of application-server failures.
* Checking logs is usually more effective than repeatedly restarting a failed service.

---

## 🎤 Interview Questions

### 1. What is Apache Tomcat?

Apache Tomcat is an open-source Java web/application server commonly used to run Java web applications.

### 2. Why does Tomcat require Java?

Tomcat is implemented in Java, so a Java runtime environment is required to execute it.

### 3. What is `server.xml`?

`server.xml` is one of Tomcat's primary configuration files. It defines server components such as connectors, ports, hosts, and services.

### 4. How do you check whether Tomcat is running?

```bash
sudo systemctl status tomcat
```

You can also check listening ports with:

```bash
sudo ss -lntp
```

### 5. What would you check if Tomcat fails to start?

I would check:

1. Tomcat service status.
2. Tomcat logs.
3. Java installation and environment.
4. Configuration files.
5. Port availability.
6. File ownership and permissions.

---

## 📌 Final Result

✅ Java environment verified
✅ Apache Tomcat installed
✅ Tomcat configured
✅ Tomcat started successfully
✅ Tomcat configured to start at boot
✅ Service and listening port verified

**Day 11 completed — Tomcat successfully installed and configured. 🚀**
