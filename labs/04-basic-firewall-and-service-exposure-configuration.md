# Lab 04: Host-Based Uncomplicated Firewall Configuration and Service Exposure Monitoring.

## 🎯 Objective
Set up a basic firewall with specific rules for security hardening and testing it, allowing only for outgoing and SSH traffic.
---
## 🛠️ Step-by-Step Implementation

### Step 1: Check current service exposure.
Via the `sudo ss -tuln` command, check current exposure of most common protocols.

<img width="1567" height="302" alt="Captura de tela 2026-10-06 112337" src="https://github.com/user-attachments/assets/71e59b0d-a761-4594-a296-a2333e92c379" />

---
### Step 2: Install and configure default UFW Policies
Initialize Uncomplicated Firewall on the machine and set the baseline: Deny all incoming connections and allow all outgoing traffic.

<img width="1562" height="316" alt="Captura de tela 2026-10-06 112458" src="https://github.com/user-attachments/assets/f4178568-87d0-48b0-8d58-ab293be113b9" />

---
### Step 3: Allow Safe Management Ports
Explicitly allow for secure shell traffic.

<img width="389" height="57" alt="Captura de tela 2026-10-06 112548" src="https://github.com/user-attachments/assets/0949fdcf-6637-45d6-a348-e6d79cc891bf" />

---
### Step 4: Enable the Firewall and Enable Logging
Turn the firewall on and enable packet logging to track blocked intrusion or scanning attempts.

<img width="1568" height="127" alt="Captura de tela 2026-10-06 112629" src="https://github.com/user-attachments/assets/f812bc7b-578d-441d-8c3c-420d867fecbf" />

---
### Step 5: Verify Firewall Logs
Via the `journalctl` command, check recent uncomplicated firewall logs.

<img width="846" height="328" alt="Captura de tela 2026-10-06 112916" src="https://github.com/user-attachments/assets/52ba7a58-4ee3-4db4-95c5-8df5cce3317a" />

---
### Step 6: Incoming Traffic Test
Test if incoming traffic is denied, as it should, per the baseline set.

Run a lightweight http.server via a `python3` script to simulate an exposed port.

<img width="1550" height="282" alt="Captura de tela 2026-10-06 114426" src="https://github.com/user-attachments/assets/0d0f57e1-2f97-4382-a967-8fb434fcc81b" />

Check if an outsider host (In this case, my real physical PC) can reach said port. Tried testing connection with the port via PowerShell.

<img width="1110" height="622" alt="Captura de tela 2026-10-06 114411" src="https://github.com/user-attachments/assets/4a131a9c-0f91-4abf-8ab7-befeafeeabdb" />
As you can see, both the TCP Connect and the Ping attempts failed/timed out, meaning the firewall is working correctly when it comes to blocking incoming traffic.

---
### Step 7: Outgoing Traffic Test
Test if the default-allow outbound policy lets the VM reach the internet.
Tried reaching google.com via the `curl` command.

<img width="1550" height="415" alt="Captura de tela 2026-10-06 114832" src="https://github.com/user-attachments/assets/e219424e-e296-413c-bfb0-b7d024a36eab" />
The HTTP status code at the top, HTTP/2 200, confirms we are able to reach it successfully.

---
### Results
Here is a final status check of the current configurations of UFW done in this lab, Firewall active, default incoming set to `deny`, outgoing set to `allow`:

<img width="1570" height="309" alt="Captura de tela 2026-10-06 115510" src="https://github.com/user-attachments/assets/1c62c122-430d-4385-9e7c-d870d2ee4bc0" />

Also note how connectivity to port 22 (SSH) is explicitly permitted.







