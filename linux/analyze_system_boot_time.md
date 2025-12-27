On Ubuntu/Linux (with **systemd**), you can analyze **system boot time** using `systemd-analyze`.

---

## 1️⃣ Overall boot time

```bash
systemd-analyze
```

**Example output:**

```
Startup finished in 3.215s (kernel) + 8.432s (userspace) = 11.647s
```

* **Kernel** → time to load the kernel
* **Userspace** → time to start services
* **Total** → full boot time

---

## 2️⃣ See which services took the longest

Install systemd-analyze by: `sudo apt install systemd`

```bash
systemd-analyze blame
```

**Example:**

```
5.432s NetworkManager.service
3.210s snapd.service
1.842s docker.service
```

Services at the top are slowing boot the most.

---

## 3️⃣ View service startup dependency chain

```bash
systemd-analyze critical-chain
```

This shows:

* Which services block others
* The **critical path** that delays boot

---

## 4️⃣ Analyze a specific service

```bash
systemctl status service_name
```

Example:

```bash
systemctl status snapd
```

---

## 5️⃣ Graphical boot chart (advanced)

Generate an SVG timeline:

```bash
systemd-analyze plot > boot-analysis.svg
```

Then open it:

```bash
xdg-open boot-analysis.svg
```

This visually shows:

* Parallel service startup
* Delays and bottlenecks

---

## 6️⃣ Tips to improve boot time

* Disable unnecessary services:

```bash
sudo systemctl disable service_name
```

* Mask services that should never start:

```bash
sudo systemctl mask service_name
```

**Be careful** disabling system services (like `networking`, `systemd-logind`).
