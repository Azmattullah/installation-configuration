On Ubuntu/Linux, you can monitor logs in real time using **`tail`** and a few related tools.

---

## 1️⃣ Monitor a log file in real time (most common)

```bash
tail -f /path/to/logfile.log
```

**Example:**

```bash
tail -f /var/log/syslog
```

* `-f` → follows the file as new lines are written
* Press **Ctrl + C** to stop

---

## 2️⃣ Show last N lines and continue monitoring

```bash
tail -n 100 -f logfile.log
```

Shows the last 100 lines, then continues live.

---

## 3️⃣ Monitor multiple log files

```bash
tail -f /var/log/syslog /var/log/auth.log
```

---

## 4️⃣ Monitor logs with filtering (grep)

Useful when logs are noisy:

```bash
tail -f logfile.log | grep ERROR
```

Or case-insensitive:

```bash
tail -f logfile.log | grep -i warning
```

---

## 5️⃣ Follow rotated logs (better for long-running monitoring)

```bash
tail -F logfile.log
```

* `-F` keeps following even if the log file is rotated (renamed/recreated)

---

## 6️⃣ System logs with `journalctl` (systemd systems)

For services managed by systemd:

### Follow system logs

```bash
journalctl -f
```

### Follow logs for a specific service

```bash
journalctl -u nginx -f
```

### Logs since last boot

```bash
journalctl -b
```

---

## 7️⃣ Colorized & interactive viewing (optional tools)

If installed:

```bash
less +F logfile.log
```

* Press **Ctrl + C** → pause
* Press **Shift + F** → resume following

---

## Common log locations

* `/var/log/syslog`
* `/var/log/auth.log`
* `/var/log/nginx/`
* `/var/log/apache2/`

