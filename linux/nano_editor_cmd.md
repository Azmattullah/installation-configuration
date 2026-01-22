Below is a **clear, step-by-step guide to using the Nano text editor** on Linux systems (Ubuntu, Debian, CentOS, Amazon Linux, etc.). This is written for 


## 1. What is Nano?

**Nano** is a simple, beginner-friendly terminal text editor. It is commonly used for editing configuration files, scripts, and notes directly from the command line.

---

## 2. Check if Nano Is Installed

Run:

```bash
nano --version
```

If not installed:

**Ubuntu / Debian**

```bash
sudo apt update && sudo apt install nano -y
```

**CentOS / RHEL / Amazon Linux**

```bash
sudo yum install nano -y
```

---

## 3. Open a File with Nano

### Open an existing file

```bash
nano filename.txt
```

### Create a new file

```bash
nano newfile.txt
```

Nano opens directly in edit mode.

---

## 4. Understanding the Nano Interface

* **Top line** → File name
* **Main area** → Editable content
* **Bottom section** → Shortcut keys
  (`^` means **Ctrl** key)

Example:

```
^O Write Out   ^X Exit   ^W Where Is   ^K Cut   ^U Paste
```

---

## 5. Basic Editing

### Type Text

* Start typing immediately
* Use arrow keys to move the cursor

### Delete Text

* **Backspace** → delete left
* **Delete** → delete right

---

## 6. Save a File (Very Important)

1. Press:

   ```
   Ctrl + O
   ```
2. Nano shows the file name
3. Press:

   ```
   Enter
   ```

File is saved.

---

## 7. Exit Nano

* Press:

  ```
  Ctrl + X
  ```

If there are unsaved changes:

* Press **Y** to save
* Press **N** to discard
* Press **Ctrl + C** to cancel exit

---

## 8. Cut, Copy, and Paste

### Cut a Line

```bash
Ctrl + K
```

### Paste a Line

```bash
Ctrl + U
```

### Select Text (Mark Mode)

1. Move cursor to start
2. Press:

   ```bash
   Ctrl + ^
   ```
3. Move cursor to select
4. Press **Ctrl + K** (cut) or **Ctrl + U** (paste)

---

## 9. Search and Replace

### Search Text

```bash
Ctrl + W
```

* Type search term
* Press **Enter**

### Replace Text

```bash
Ctrl + \
```

* Enter search term
* Enter replacement text
* Press **Y** to confirm replacement

---

## 10. Go to a Specific Line Number

```bash
Ctrl + _
```

* Enter line number
* Press **Enter**

Useful for logs and config files.

---

## 11. Enable Line Numbers (Optional)

Temporary (inside Nano):

```bash
Alt + Shift + 3
```

Permanent:

```bash
nano ~/.nanorc
```

Add:

```bash
set linenumbers
```

Save and exit.

---

## 12. Open File as Root (Very Common)

For system files:

```bash
sudo nano /etc/nginx/nginx.conf
```

---

## 13. Most Used Nano Shortcuts (Quick Reference)

| Action     | Shortcut |
| ---------- | -------- |
| Save       | Ctrl + O |
| Exit       | Ctrl + X |
| Search     | Ctrl + W |
| Replace    | Ctrl + \ |
| Cut line   | Ctrl + K |
| Paste      | Ctrl + U |
| Select     | Ctrl + ^ |
| Go to line | Ctrl + _ |
| Help       | Ctrl + G |

---

## 14. When to Use Nano vs Vim

* **Nano** → Quick edits, beginners, config changes
* **Vim** → Advanced editing, power users

---


<br><br>

# **Nano Editor – 1-Page Cheat Sheet**

**Legend:** `^` = **Ctrl**, `M` = **Alt**

---

## File Operations

| Action              | Shortcut            |
| ------------------- | ------------------- |
| Open file           | `nano file.txt`     |
| Save (Write Out)    | `^O` → Enter        |
| Exit                | `^X`                |
| Save & Exit         | `^O` → Enter → `^X` |
| Exit without saving | `^X` → `N`          |

---

## Navigation

| Action            | Shortcut   |
| ----------------- | ---------- |
| Move cursor       | Arrow keys |
| Beginning of line | `^A`       |
| End of line       | `^E`       |
| Next page         | `^V`       |
| Previous page     | `^Y`       |
| Go to line/column | `^_`       |
| First line        | `M-\`      |
| Last line         | `M-/`      |

---

## Editing

| Action                   | Shortcut           |
| ------------------------ | ------------------ |
| Cut current line         | `^K`               |
| Paste (Uncut)            | `^U`               |
| Delete char (left/right) | Backspace / Delete |
| Undo                     | `M-U`              |
| Redo                     | `M-E`              |

---

## Select / Copy

| Action                 | Shortcut           |
| ---------------------- | ------------------ |
| Start selection (Mark) | `^6` or `^Shift+^` |
| Cut selection          | `^K`               |
| Paste selection        | `^U`               |

---

## Search & Replace

| Action      | Shortcut   |
| ----------- | ---------- |
| Search      | `^W`       |
| Search next | `M-W`      |
| Replace     | `^\`       |
| Replace all | `^\` → `A` |

---

## Display & Help

| Action                     | Shortcut |
| -------------------------- | -------- |
| Help                       | `^G`     |
| Show line numbers (toggle) | `M-#`    |
| Refresh screen             | `^L`     |

---

## Useful Launch Options

```bash
nano +25 file.txt        # open at line 25
nano -l file.txt         # show line numbers
sudo nano /path/file     # edit as root
```

---

## Configuration (Persistent)

Edit Nano config:

```bash
nano ~/.nanorc
```

Common options:

```text
set linenumbers
set mouse
set tabsize 4
```

---

## Most-Used Shortcuts (Memory Aid)

```
Save   : ^O
Exit   : ^X
Search : ^W
Cut    : ^K
Paste  : ^U
Replace: ^\
Line   : ^_
Help   : ^G
```
