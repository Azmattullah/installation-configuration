In Ubuntu (and most Linux systems), you can use **`find`**.

### Find files modified in the last 24 hours

```bash
find /path/to/search -type f -mtime -1
```

**Example (current directory and subdirectories):**

```bash
find . -type f -mtime -1
```

### Explanation

* `-type f` → only files (not directories)
* `-mtime -1` → modified less than 1 day (24 hours) ago
* `.` → current directory (replace with any path, e.g. `/home/user`)

### If you want *exactly* the last 24 hours (more precise)

Using minutes instead of days:

```bash
find . -type f -mmin -1440
```

### Show details (ls-style output)

```bash
find . -type f -mtime -1 -exec ls -lh {} \;
```

### Exclude certain directories (example: `.git`)

```bash
find . -type f -mtime -1 -not -path "*/.git/*"
```