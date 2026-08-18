# 👥 Day 06 – Linux User and Group Management

## 📌 Scenario

The Nautilus production support team needed to manage user access on an application server.

A new user account had to be created and associated with the appropriate group so that the user could access resources according to the team's requirements.

---

## 🎯 Objectives

* Create the required Linux user
* Create or use the required group
* Add the user to the appropriate group
* Verify user and group membership
* Follow the principle of least privilege

---

## 🛠️ Tasks Performed

### ✅ 1. Check Existing Users and Groups

Reviewed the existing account and group configuration:

```bash
id <username>
```

and:

```bash
getent group
```

This helped confirm the current state before making changes.

---

### ✅ 2. Create the Required Group

Created the required group when it was not already available:

```bash
sudo groupadd <groupname>
```

---

### ✅ 3. Create the User

Created the required Linux user:

```bash
sudo useradd <username>
```

---

### ✅ 4. Add User to Group

Added the user to the required supplementary group:

```bash
sudo usermod -aG <groupname> <username>
```

The `-aG` combination is important because:

* `-G` specifies supplementary groups
* `-a` appends the group instead of replacing existing supplementary group memberships

---

### ✅ 5. Verify Group Membership

Checked the user's groups:

```bash
id <username>
```

or:

```bash
groups <username>
```

Confirmed that the required group was present.

---

## 🔐 Understanding Linux Groups

Linux groups are commonly used to manage access to shared resources.

Instead of granting permissions individually to every user, administrators can:

```text
Users
  │
  ├── User A ──┐
  ├── User B ──┼──> Development Group
  └── User C ──┘
                    │
                    ▼
              Shared Resources
```

This makes permission management easier and more consistent.

---

## ⚠️ Common Mistakes to Avoid

* Using `usermod -G` without `-a`
* Accidentally removing existing supplementary groups
* Giving users unnecessary group memberships
* Creating duplicate groups
* Forgetting to verify the final configuration
* Assuming a group change is immediately reflected in an already-open login session

---

## 🧠 Key Learnings

* Linux groups simplify permission management.
* Users can belong to multiple supplementary groups.
* `usermod -aG` is commonly used to add a user without removing existing supplementary groups.
* Group membership should follow the principle of least privilege.
* Always verify user and group configuration after making changes.

---

## 🎤 Interview Questions

### Q1. What is the purpose of Linux groups?

Groups allow administrators to manage permissions for multiple users collectively.

### Q2. What does `usermod -aG` do?

It adds a user to a supplementary group while preserving their existing supplementary group memberships.

### Q3. What happens if you use `usermod -G` without `-a`?

The user's existing supplementary groups can be replaced by the groups specified with `-G`.

### Q4. How can you check a user's group membership?

```bash
id <username>
```

or:

```bash
groups <username>
```

### Q5. Why is least privilege important?

Users should have only the permissions and access required to perform their responsibilities, reducing security risk.

---

## 📌 Final Result

```text
Linux Server
     │
     ▼
User Created
     │
     ▼
Required Group
     │
     ▼
User Added to Group
     │
     ▼
Permissions Managed Through Group
```

👥 **Linux user and group access successfully configured.**

✅ **Day 06 Completed Successfully** 🚀
