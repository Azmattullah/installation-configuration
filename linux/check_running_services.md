On Ubuntu/Linux, checking running services depends on whether your system uses **systemd** (most modern Ubuntu versions) or the older **init** system. On Ubuntu 16.04+ it’s usually **systemd**.

Here’s how to check:

---

## 1️⃣ List all services (active or inactive)

```bash
systemctl list-units --type=service
```

* Shows **all services** with their status (`active`, `inactive`, `failed`)
* Columns: UNIT, LOAD, ACTIVE, SUB, DESCRIPTION

---

## 2️⃣ List only active (running) services

```bash
systemctl list-units --type=service --state=running
```

* Shows only currently **running services**

---

## 3️⃣ Check status of a specific service

```bash
systemctl status service_name
```

**Example:**

```bash
systemctl status apache2
```

* Shows if it’s running, enabled on boot, and recent logs

---

## 4️⃣ Check which services are enabled at startup

```bash
systemctl list-unit-files --type=service | grep enabled
```

* Useful to see which services start automatically

---

## 5️⃣ Alternative: using `service` command (older style)

```bash
service --status-all
```

* Shows a list of services with symbols:

  * `[ + ]` → running
  * `[ - ]` → stopped
  * `[ ? ]` → unknown status

---

💡 **Tip:** You can combine commands to quickly see running services and their ports:

```bash
ss -tuln | grep LISTEN
```

or

```bash
sudo lsof -i -P -n | grep LISTEN
```

