````markdown
# 01 - Linux User Management

Hands-on Linux user and group management lab using RHEL and Ubuntu.

## 🎯 Objectives

In this lab, I practice:

- Creating users
- Creating groups
- Adding users to groups
- Managing passwords
- Managing sudo access
- Locking and unlocking user accounts
- Checking user and group information
- Managing user accounts

---

## 🖥️ Lab Environment

- RHEL
- Ubuntu
- Bash

---

## 1. Check Current User

Check the current username:

```bash
whoami
````

Check UID, GID and group membership:

```bash
id
```

Check groups:

```bash
groups
```

---

## 2. Create a User

Create a user with a home directory:

```bash
sudo useradd -m devuser
```

Verify:

```bash
id devuser
```

Check the `/etc/passwd` entry:

```bash
grep '^devuser:' /etc/passwd
```

Check the home directory:

```bash
ls -ld /home/devuser
```

---

## 3. Set User Password

Set a password for `devuser`:

```bash
sudo passwd devuser
```

Switch to the user:

```bash
su - devuser
```

Verify:

```bash
whoami
```

Check the current directory:

```bash
pwd
```

Return to the previous user:

```bash
exit
```

---

## 4. Create a Group

Create a group named `devops`:

```bash
sudo groupadd devops
```

Verify:

```bash
getent group devops
```

---

## 5. Add User to Group

Add `devuser` to the `devops` group:

```bash
sudo usermod -aG devops devuser
```

Verify:

```bash
id devuser
```

or:

```bash
groups devuser
```

### Important

Use:

```bash
usermod -aG
```

The `-aG` option appends the supplementary group without removing the user's existing supplementary groups.

---

## 6. Check User Information

Display user information:

```bash
getent passwd devuser
```

Check UID, GID and groups:

```bash
id devuser
```

Check group membership:

```bash
groups devuser
```

---

## 7. Change User Shell

Check available shells:

```bash
cat /etc/shells
```

Change the user's shell to Bash:

```bash
sudo usermod -s /bin/bash devuser
```

Verify:

```bash
getent passwd devuser
```

---

## 8. Lock a User Account

Lock the account:

```bash
sudo passwd -l devuser
```

Check account status:

```bash
sudo passwd -S devuser
```

---

## 9. Unlock a User Account

Unlock the account:

```bash
sudo passwd -u devuser
```

Verify:

```bash
sudo passwd -S devuser
```

---

## 10. Configure Sudo Access

### RHEL

Add the user to the `wheel` group:

```bash
sudo usermod -aG wheel devuser
```

### Ubuntu

Add the user to the `sudo` group:

```bash
sudo usermod -aG sudo devuser
```

Verify:

```bash
id devuser
```

---

## 11. Test Sudo Access

Switch to the user:

```bash
su - devuser
```

Test sudo access:

```bash
sudo whoami
```

Expected output:

```text
root
```

Return:

```bash
exit
```

---

# 🧪 Lab Exercise

Perform the following tasks without looking at the commands above.

### Task 1

Create a user:

```text
appuser
```

### Task 2

Create a group:

```text
appteam
```

### Task 3

Add `appuser` to `appteam`.

### Task 4

Set a password for `appuser`.

### Task 5

Verify the user:

```bash
id appuser
```

### Task 6

Give `appuser` sudo access using the appropriate group for your Linux distribution.

### Task 7

Switch to `appuser` and verify:

```bash
whoami
```

Then:

```bash
sudo whoami
```

Expected:

```text
appuser
root
```

### Task 8

Lock the account and verify its status.

### Task 9

Unlock the account and verify again.

### Task 10

Remove the test user.

For example:

```bash
sudo userdel -r appuser
```

---

## 🔍 Useful Verification Commands

```bash
id username
```

```bash
groups username
```

```bash
getent passwd username
```

```bash
getent group groupname
```

```bash
sudo passwd -S username
```

---

## 📌 Key Commands

| Command    | Purpose                     |
| ---------- | --------------------------- |
| `useradd`  | Create user                 |
| `usermod`  | Modify user                 |
| `userdel`  | Delete user                 |
| `passwd`   | Manage password             |
| `groupadd` | Create group                |
| `id`       | Display UID, GID and groups |
| `groups`   | Display group membership    |
| `getent`   | Query users and groups      |
| `su`       | Switch user                 |

---

## 🎯 What I Practiced

* Linux user management
* Group management
* Password management
* Sudo administration
* Account locking and unlocking
* User verification
* Basic Linux account lifecycle management

---

📌 This lab is part of my Linux Administration learning journey.

````
