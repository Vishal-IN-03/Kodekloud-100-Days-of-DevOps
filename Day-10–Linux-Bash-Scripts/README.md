# 🐚 Day 10 – Linux Bash Scripts

## 📌 Scenario

The Nautilus DevOps team needs a simple Bash script to automate a routine task on an application server.

The script should be created in the required location, made executable, and tested to ensure it produces the expected output.

---

## 🎯 Objectives

* Create a Bash script in the required location.
* Use the Bash shell correctly.
* Add the required script logic.
* Give the script executable permissions.
* Execute the script successfully.
* Verify the expected output.

---

## 🛠️ Tasks Performed

### 1. Create the Bash Script

Created the required shell script using a text editor.

A Bash script normally begins with a **shebang**:

```bash
#!/bin/bash
```

The shebang tells Linux which interpreter should be used to execute the script.

---

### 2. Add the Required Script Logic

Added the required commands to perform the task.

Example structure:

```bash
#!/bin/bash

# Script logic goes here
echo "Hello from Bash"
```

---

### 3. Make the Script Executable

Added execute permission to the script:

```bash
chmod +x /path/to/script.sh
```

Verified the permissions:

```bash
ls -l /path/to/script.sh
```

The permissions should contain `x`, indicating that the script can be executed.

---

### 4. Execute the Script

Executed the script:

```bash
./script.sh
```

The script executed successfully and produced the expected output.

---

## 🔍 Verification

Verified the following:

```bash
ls -l /path/to/script.sh
```

Confirmed that the script had executable permissions.

Then executed it:

```bash
./script.sh
```

The expected output was displayed successfully.

---

## 🚨 Problems / Troubleshooting

A common issue when working with Bash scripts is receiving:

```text
Permission denied
```

This usually means the script does not have execute permission.

The issue can be fixed with:

```bash
chmod +x script.sh
```

Another common problem is running the script from the wrong directory or using an incorrect path.

---

## 🧠 Key Learnings

* Bash scripts automate repetitive Linux tasks.
* `#!/bin/bash` specifies Bash as the script interpreter.
* `chmod +x` grants execute permission.
* `./script.sh` executes a script from the current directory.
* File permissions are important when running scripts.
* Scripts should always be tested after creation to verify their behavior.

---

## 🎤 Interview Questions

### 1. What is a Bash script?

A Bash script is a text file containing a sequence of commands that can be executed by the Bash shell.

### 2. What does `#!/bin/bash` mean?

It is a **shebang** that tells the operating system to use `/bin/bash` to interpret the script.

### 3. How do you make a script executable?

```bash
chmod +x script.sh
```

### 4. How do you execute a Bash script?

One common method is:

```bash
./script.sh
```

Another method is:

```bash
bash script.sh
```

The first method requires execute permission, while the second directly invokes Bash to interpret the file.

### 5. How do you check a script's permissions?

```bash
ls -l script.sh
```

---

## 📌 Final Result

✅ Bash script created
✅ Required logic added
✅ Execute permission configured
✅ Script executed successfully
✅ Output verified

**Day 10 completed — Linux Bash scripting successfully performed. 🚀**
