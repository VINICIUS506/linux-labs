# Lab 04: Host-Based Uncomplicated Firewall Configuration and Service Exposure Monitoring.

## 🎯 Objective
Configure baseline firewall security using UFW, enforce default deny-inbound and allow-outbound policies, permit secure SSH management access, and validate rule enforcement through active network testing and log verification.

---
## 🛠️ Step-by-Step Implementation

### Step 1: Check current Service Exposure
Inspected open listening ports and active network socket statistics using the `sudo ss -tuln` command to establish an exposure baseline prior to configuring firewall rules.

<img width="1567" height="302" alt="Captura de tela 2026-10-06 112337" src="https://github.com/user-attachments/assets/71e59b0d-a761-4594-a296-a2333e92c379" />

---
### Step 2: Install and configure default UFW Policies
Initialized UFW default security policies to establish a hardened baseline: deny all incoming connections while allowing all outgoing traffic.

<img width="1562" height="316" alt="Captura de tela 2026-10-06 112458" src="https://github.com/user-attachments/assets/f4178568-87d0-48b0-8d58-ab293be113b9" />

---
### Step 3: Allow Safe Management Ports
Explicitly permitted inbound SSH traffic to prevent lockouts and ensure secure remote administrative access.

<img width="389" height="57" alt="Captura de tela 2026-10-06 112548" src="https://github.com/user-attachments/assets/0949fdcf-6637-45d6-a348-e6d79cc891bf" />

---
### Step 4: Enable the Firewall and Packet Logging
Enabled UFW on the system and turned on packet logging to track rejected connection attempts and potential network scanning activity.

<img width="1568" height="127" alt="Captura de tela 2026-10-06 112629" src="https://github.com/user-attachments/assets/f812bc7b-578d-441d-8c3c-420d867fecbf" />

---
### Step 5: Verify Firewall Logs
Inspected system log entries using `journalctl` to confirm that UFW packet events are being correctly recorded by the logging service.

<img width="846" height="328" alt="Captura de tela 2026-10-06 112916" src="https://github.com/user-attachments/assets/52ba7a58-4ee3-4db4-95c5-8df5cce3317a" />

---
### Step 6: Incoming Traffic Test
Tested inbound traffic blocking by starting a temporary Python HTTP server (python3 -m http.server) on the virtual machine.

<img width="1550" height="282" alt="Captura de tela 2026-10-06 114426" src="https://github.com/user-attachments/assets/0d0f57e1-2f97-4382-a967-8fb434fcc81b" />

Attempted to connect to the exposed port from an external host (my physical PC) using PowerShell.

<img width="1110" height="622" alt="Captura de tela 2026-10-06 114411" src="https://github.com/user-attachments/assets/4a131a9c-0f91-4abf-8ab7-befeafeeabdb" />

As you can see, both the TCP Connect and the Ping attempts failed/timed out, meaning the firewall is working correctly when it comes to blocking incoming traffic.

---
### Step 7: Outgoing Traffic Test
Verified that the default-allow outbound policy permits network connectivity from the VM to external web services by querying Google via `curl`.

<img width="1550" height="415" alt="Captura de tela 2026-10-06 114832" src="https://github.com/user-attachments/assets/e219424e-e296-413c-bfb0-b7d024a36eab" />

The HTTP status code at the top, HTTP/2 200, confirms outbound HTTP access.

---
### Results
The detailed status check (sudo ufw status verbose) confirms that UFW is active with a default deny (incoming) and allow (outgoing) baseline, explicitly allowing port 22 (SSH) connections:

<img width="1570" height="309" alt="Captura de tela 2026-10-06 115510" src="https://github.com/user-attachments/assets/1c62c122-430d-4385-9e7c-d870d2ee4bc0" />








