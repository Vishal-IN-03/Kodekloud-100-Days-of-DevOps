# 👤 Day 02 – Linux User Account Expiry

## 📌 Scenario

The Nautilus production support team needed to create a temporary Linux user account on an application server.

The account was required for a limited period, so an **account expiry date** had to be configured to ensure the user would no longer be able to use the account after the specified date.

---

## 🎯 Objectives

* Create the required Linux user
* Configure an account expiry date
* Ensure the account is temporary
* Verify the expiry configuration

---

## 🛠️ Tasks Performed

### ✅ 1. Create the User

Created the required user account on the designated application server.

```bash
sudo useradd <username>
```

---

### ✅ 2. Configure Account Expiry

Configured the account with the required expiry date.

```bash
sudo chage -E <YYYY-MM-DD> <username>
```

The expiry date controls when the user's account becomes inactive.

---

### ✅ 3. Verify Account Information

Checked the account configuration:

```bash
sudo chage -l <username>
```

Verified that the required expiry date was correctly configured.

---

## 🔍 Understanding Account Expiry

Linux account expiry is different from password expiry.

### Account expiry

Controls whether the **user account itself** can be used after a specific date.

### Password expiry

Controls when the **user's password** needs to be changed.

For temporary users, account expiry is useful because access can automatically stop after the required period.

---

## ⚠️ Common Mistakes to Avoid

* Setting the wrong expiry date
* Confusing account expiry with password expiry
* Forgetting to verify the configuration
* Creating the account on the wrong server
* Manually deleting temporary users when automatic expiry is sufficient

---

## 🧠 Key Learnings

* Linux provides built-in mechanisms for managing temporary accounts.
* Account expiry is an important security control.
* `chage` can be used to manage account aging and expiry settings.
* Access controls should be configured according to the user's actual requirement.
* Always verify security-related changes after applying them.

---

## 🎤 Interview Questions

### Q1. What is account expiry in Linux?

Account expiry defines the date after which a Linux user account becomes inactive.

### Q2. Which command can configure account expiry?

```bash
chage -E <YYYY-MM-DD> <username>
```

### Q3. How can you check a user's expiry information?

```bash
chage -l <username>
```

### Q4. What is the difference between account expiry and password expiry?

Account expiry disables the account after a specified date, while password expiry controls the lifetime of the user's password.

### Q5. Why is account expiry useful for temporary users?

It automatically limits access to the required period and reduces the risk of forgotten accounts remaining active.

---

## 📌 Final Result

```text
Temporary Linux User
        │
        ▼
Account Expiry Configured
        │
        ▼
Access available only
until the specified date
        │
        ▼
Automatic account expiration
```

✅ **Day 02 Completed Successfully** 🚀
