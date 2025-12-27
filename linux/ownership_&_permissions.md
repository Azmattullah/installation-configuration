In Ubuntu/Linux, ownership and permissions are changed with **`chown`** and **`chmod`**.

---

## 1️⃣ Change file ownership (`chown`)

### Change owner

```bash
sudo chown username filename
```

### Change owner and group

```bash
sudo chown username:groupname filename
```

### Change only group

```bash
sudo chown :groupname filename
```

### Recursive (for directories)

```bash
sudo chown -R username:groupname directory/
```

---

## 2️⃣ Change file permissions (`chmod`)

### Using numeric (octal) mode

```bash
chmod 755 filename
```

**Common values:**

| Permission | Meaning     |
| ---------- | ----------- |
| `755`      | rwx r-x r-x |
| `644`      | rw- r-- r-- |
| `700`      | rwx --- --- |
| `600`      | rw- --- --- |

---

### Using symbolic mode

```bash
chmod u+rwx,g+rx,o+rx filename
```

**Symbols:**

* `u` → owner
* `g` → group
* `o` → others
* `+` add, `-` remove, `=` set

**Examples:**

```bash
chmod u+x script.sh        # add execute for owner
chmod go-w filename        # remove write from group & others
chmod a+r file.txt         # add read for all
```

---

## 3️⃣ Change permissions recursively

```bash
chmod -R 755 directory/
```

---

## 4️⃣ Check current ownership & permissions

```bash
ls -l filename
```

Output example:

```
-rwxr-xr-- 1 user group 1234 file.txt
```

---

## ⚠️ Notes

* Use **`sudo`** if you don’t own the file
* Be careful with `-R` on system directories