# Lab 01: Ubuntu Desktop Installation & First Boot

## 🎯 Objective
Deploy a fresh Ubuntu 26.04 LTS machine into Oracle VirtualBox, configure basic installation options, and verify successful boot into the GNOME Display Manager (GDM).

---
## 🛠️ Step-by-Step Implementation
### Step 1: Bootloader & GRUB Selection
Selected the initial installation media entry from the GRUB bootloader to start the live OS session.

> <img width="742" height="418" alt="Captura de tela 2026-08-18 152457" src="https://github.com/user-attachments/assets/ead51bbd-eb62-4042-84dd-f10c51c4ba72" />
---
### Step 2: System Service Initialization
Verified the boot sequence as `systemd` initialized essential background services (`cloud-init`, `snapd`, and `gdm`).

> <img width="1306" height="813" alt="Captura de tela 2026-08-18 152741" src="https://github.com/user-attachments/assets/56d23fe9-f3fe-4b52-8314-25daef2711dd" />

---
### Step 3: Language & Localization Setup
As you can see, the default installer booted up. Selected **English** as the primary OS language to ensure standardized system paths and log outputs.

> <img width="1287" height="800" alt="Captura de tela 2026-08-18 152924" src="https://github.com/user-attachments/assets/1bcbcf7c-2d1f-4a7d-9401-843261f4b67b" />


---

### Step 4: Disk Partitioning & Installation Review
Confirmed the disk setup using an erased virtual disk layout (`sda1` boot / `sda2` ext4 root) before executing the installation.

> <img width="1295" height="808" alt="Captura de tela 2026-08-18 153544" src="https://github.com/user-attachments/assets/92a87ff2-982b-4a36-814a-5aa50f68ec50" />


---

### Step 5: First Boot & User Authentication
Verified the GNOME Display Manager (GDM) login interface after the initial reboot, authenticating with the local account (`vini`).

> <img width="1303" height="818" alt="Captura de tela 2026-08-18 155432" src="https://github.com/user-attachments/assets/a195bd9d-a609-45a3-8fc5-a2aafb2381fe" />


---

### Step 6: Desktop Session Verification
Successfully loaded into the GNOME desktop environment, confirming system stability and readiness for post-installation tasks.

> <img width="1293" height="823" alt="Captura de tela 2026-08-18 155550" src="https://github.com/user-attachments/assets/6979fd0e-fd55-4c1c-9e84-099d9ec28f06" />



