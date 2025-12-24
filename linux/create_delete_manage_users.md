# Linux User Management Documentation



## Creating Users

### Basic User Creation

```bash
useradd azmat
passwd azmat
```

* Creates a user account named `azmat`
* Requires setting a password separately

### Interactive Method (Distro-dependent)

```bash
adduser azmat
```

* More user-friendly and interactive
* Automatically sets home directory, password, and user details

### What Gets Created

* Home directory: `/home/azmat` (unless disabled)
* User records:

  * `/etc/passwd`
  * `/etc/shadow`
  * `/etc/group`
* Assigned:

  * UID/GID
  * Default shell

---

## Creating Users with Custom Options

```bash
useradd -m -s /bin/bash -G developers -c "azmat Dev" azmat
```

**Options explained:**

* `-m` → Create home directory
* `-s` → Assign login shell
* `-G` → Add to supplementary groups
* `-c` → Comment / full name

Set password:

```bash
passwd azmat
```

Force password change at next login:

```bash
chage -d 0 azmat
```

---

## Managing Users

### Change User Shell

```bash
usermod -s /bin/bash azmat
```

### Add User to a Group (e.g., sudo)

```bash
usermod -aG sudo azmat
```

⚠️ Always use `-aG` to avoid removing existing group memberships.

---

## Deleting Users

### Delete User Only

```bash
userdel azmat
```

### Delete User and Home Directory

```bash
userdel -r azmat
```

---

## Locking and Unlocking Accounts

### Lock User

```bash
passwd -l azmat
```

### Unlock User

```bash
passwd -u azmat
```

Useful for temporary access suspension without deleting the account.

---

## Viewing User Information

### Display UID, GID, and Groups

```bash
id azmat
```

### View User Entry

```bash
getent passwd azmat
```

✔️ `getent` works for local users and LDAP/AD users.

---

## Important System Files

| File              | Purpose                        |
| ----------------- | ------------------------------ |
| `/etc/passwd`     | Basic user account information |
| `/etc/shadow`     | Encrypted passwords and aging  |
| `/etc/group`      | Group definitions              |
| `/etc/login.defs` | Default user creation settings |

---

## Enterprise / Real-World Practices

* User management is often automated using:

  * Shell scripts
  * Ansible
  * LDAP / Active Directory
* Centralized authentication may not store users in `/etc/passwd`
* Always audit user access regularly in production systems

---
