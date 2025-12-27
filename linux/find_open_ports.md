On Ubuntu/Linux, there are several ways to find **open ports** on your system. Here are the most common and reliable methods:

---

## 1️⃣ Using `ss` (socket statistics, recommended)

```bash
ss -tuln
```

**Explanation:**

* `-t` → TCP sockets
* `-u` → UDP sockets
* `-l` → listening (open) ports
* `-n` → show numeric ports (not names)

**Example output:**

```
Netid  State   Recv-Q Send-Q Local Address:Port  Peer Address:Port
tcp    LISTEN  0      128     0.0.0.0:22        0.0.0.0:*  
tcp    LISTEN  0      100     127.0.0.1:3306    0.0.0.0:*  
udp    UNCONN  0      0       0.0.0.0:123       0.0.0.0:*  
```

* Here, **22** (SSH) and **3306** (MySQL) are open TCP ports.

---

## 2️⃣ Using `netstat` (if installed)

```bash
sudo netstat -tulnp
```

**Explanation:**

* `-t` → TCP
* `-u` → UDP
* `-l` → listening
* `-n` → numeric addresses
* `-p` → show process ID/program name

---

## 3️⃣ Using `lsof`

```bash
sudo lsof -i -P -n
```

**Explanation:**

* `-i` → network files
* `-P` → show ports numerically
* `-n` → don’t resolve hostnames

You can filter only **listening ports**:

```bash
sudo lsof -i -P -n | grep LISTEN
```

---

## 4️⃣ Using `nmap` (port scanner, optional)

If you want to scan your machine from **outside** or locally:

```bash
sudo apt install nmap
sudo nmap -sT -O localhost
```

* `-sT` → TCP connect scan
* `-O` → detect OS

This will show **open ports and the service running**.

---

✅ **Quick tip:** For checking if a specific port is open (e.g., 8080):

```bash
ss -tuln | grep 8080
```

---