# 👤 Linux User Management – Complete Guide (User, su, sudo & Permissions)

![Linux](https://img.shields.io/badge/Linux-Admin-blue)
![DevOps](https://img.shields.io/badge/DevOps-Ready-green)
![Interview](https://img.shields.io/badge/Interview-Preparation-orange)

> A production-ready, interview-focused guide to **Linux User Management** covering user creation, passwords, groups, home directories, configuration files, and switching users using `su` and `sudo`.

---

## 📌 Table of Contents

1. [Overview of User and Permission Management](#overview-of-user-and-permission-management)
2. [Types of Users](#types-of-users)
3. [Using `useradd` Command](#using-useradd-command)
4. [Setting User Passwords](#setting-user-passwords)
5. [Managing User Groups](#managing-user-groups)
6. [Removing Users](#removing-users)
7. [Introduction to Affected Files](#introduction-to-affected-files)
8. [User Home Directories](#user-home-directories)
9. [Configuration Files](#configuration-files)
10. [Switching Between Users](#switching-between-users)
11. [Using `su` Command](#using-su-command)
12. [Using `sudo` Command](#using-sudo-command)
13. [Hands-on Labs](#hands-on-labs)
14. [Interview Practice Questions](#interview-practice-questions)
15. [Quick Revision Cheat Sheet](#quick-revision-cheat-sheet)

---

## 🧭 Overview of User and Permission Management

Linux is a **multi-user operating system**. User management ensures:
- Secure access control
- Isolation between users
- Auditing and accountability

**Real-time Use Case:**
On production servers, each engineer gets a personal account with controlled sudo access.

---

## 👥 Types of Users

| Type | Description |
|-----|-------------|
| Root user | Superuser with UID 0 |
| System users | Service accounts (nginx, mysql, docker) |
| Normal users | Human login users |

Check UID type:
```bash
id user1
```

---

## ➕ Using `useradd` Command

### Basic User Creation
```bash
sudo useradd user1
```

### Create with Home Directory
```bash
sudo useradd -m user1
```

### Create with Custom Shell
```bash
sudo useradd -s /bin/bash user1
```

### Create with UID and Group
```bash
sudo useradd -u 2001 -g devops user1
```

**Use Case:** Creating application users for running services.

---

## 🔑 Setting User Passwords

```bash
sudo passwd user1
```

Force password change on first login:
```bash
sudo chage -d 0 user1
```

Lock / Unlock password:
```bash
sudo passwd -l user1
sudo passwd -u user1
```

---

## 👨‍👩‍👧 Managing User Groups

### Add User to Group
```bash
sudo usermod -aG docker user1
```

### Change Primary Group
```bash
sudo usermod -g developers user1
```

### View Groups
```bash
groups user1
id user1
```

**Use Case:** Grant docker access without root privileges.

---

## ➖ Removing Users

### Delete User Only
```bash
sudo userdel user1
```

### Delete User with Home Directory
```bash
sudo userdel -r user1
```

**Use Case:** Cleanup resigned employee accounts.

---

## 📂 Introduction to Affected Files

| File | Purpose |
|-----|--------|
| /etc/passwd | User account info |
| /etc/shadow | Encrypted passwords |
| /etc/group | Group info |
| /etc/gshadow | Group passwords |

View safely:
```bash
sudo vipw
sudo vigr
```

---

## 🏠 User Home Directories

Default location:
```bash
/home/username
```

Create user with home:
```bash
sudo useradd -m user1
```

Change home directory:
```bash
sudo usermod -d /data/user1 -m user1
```

---

## ⚙️ Configuration Files

| File | Description |
|-----|-------------|
| /etc/login.defs | Default UID, password policy |
| /etc/default/useradd | Default settings |
| /etc/skel | Template for new home dirs |

**Use Case:** Enforcing default shell and directory structure.

---

## 🔄 Switching Between Users

### Using `su` (Switch User)
```bash
su - user1
```

Return to root:
```bash
exit
```

---

## 🔐 Using `su` Command

| Command | Meaning |
|--------|--------|
| su | Switch to root |
| su - user1 | Switch with environment |

**Use Case:** Temporarily becoming another user for testing permissions.

---

## 🛡 Using `sudo` Command

### Run Command as Root
```bash
sudo systemctl restart nginx
```

### Switch to Root Shell
```bash
sudo -i
```

### Edit sudoers Safely
```bash
sudo visudo
```

Example sudo rule:
```text
user1 ALL=(ALL) NOPASSWD: /bin/systemctl
```

**Use Case:** Grant limited admin rights without sharing root password.

---

## 🧪 Hands-on Labs

### Lab 1: User Lifecycle
1. Create user `dev1` with home directory
2. Set password and force change on login
3. Add to `developers` group
4. Lock the account
5. Delete user with home

---

### Lab 2: Sudo Practice
1. Create user `ops1`
2. Give sudo access for `systemctl` only
3. Test restarting nginx

---

## 🎯 Interview Practice Questions

### Conceptual
1. Difference between `su` and `sudo`?
2. What is stored in `/etc/passwd` vs `/etc/shadow`?
3. What happens if home directory is deleted but user exists?

### Scenario-Based
1. User cannot run sudo – how to troubleshoot?
2. Create a user who can restart nginx but nothing else.
3. Migrate a user’s home directory to new disk.

---

## 📌 Quick Revision Cheat Sheet

| Task | Command |
|-----|--------|
| Create user | `useradd -m user1` |
| Set password | `passwd user1` |
| Add to group | `usermod -aG docker user1` |
| Delete user | `userdel -r user1` |
| Switch user | `su - user1` |
| Run as root | `sudo command` |

---

## 🚀 Suggested Next Topics

- File permissions & ACLs
- umask and default permissions
- Central auth (LDAP, FreeIPA)
- Auditing with `last`, `faillog`

---

## 🤝 Contributing

Add:
- More labs
- Troubleshooting cases
- Advanced sudo rules

---

## 📄 License

MIT License

