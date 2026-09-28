# Lab 03: User & Group Management, Shared Directories, and Sudo Privileges

## 🎯 Objective
Create and configure a new group and users, manage access control, apply file permissions and specify administrative privileges via `sudoers`.

---
## 🛠️ Step-by-Step Implementation

### Step 1: Group Creation
Created new group `sysadmins` and verified its creation.

<img width="1919" height="1033" alt="Captura de tela 2026-09-28 165041" src="https://github.com/user-attachments/assets/14e8cb9f-267d-47d7-b763-a3a64f6285d9" />

---
### Step 2: Directory and chown.
Created an exclusive directory for members of the group and changed the owner of said directory to root and sysadmins group via the `chown` command.

Also used `chmod` to change file permissions.

<img width="1581" height="877" alt="Captura de tela 2026-09-28 165838" src="https://github.com/user-attachments/assets/53c85063-7f47-4bad-af46-bf491f437be2" />

---
### Step 3: User creation and assignment.
Provisioned a senior administrator, that is planned to have full sudo privileges, and a jr administration, planned to only have access to a few privileged commands. Added both to the newly created `sysadmins` group.

<img width="1576" height="879" alt="Captura de tela 2026-09-28 170620" src="https://github.com/user-attachments/assets/a6c1cbab-e2c9-4ff5-9a0e-df2abc95d862" />

---
### Step 4: Sudo Privileges.
Accessed `/etc/sudoers` via the `sudo visudo` command to confirm full system privileges to sr-admin and specify the limited privileges of jr-admin.

<img width="1580" height="869" alt="Captura de tela 2026-09-28 172129" src="https://github.com/user-attachments/assets/a323c37b-082a-4788-9fe7-36e200f6efe7" />

---
### Step 5: Passwords.
Set passwords for sr-admin and jr-admin.

<img width="1584" height="877" alt="Captura de tela 2026-09-28 172626" src="https://github.com/user-attachments/assets/1b06940f-d57a-4d89-a0b3-c02998cc37aa" />

---
### Step 6: File creation test.
Tested if the newly added users could create files in their exclusive directory. Confirmed that they could and also that vini (our main original user) couldn't.

<img width="1567" height="859" alt="Captura de tela 2026-09-28 172859" src="https://github.com/user-attachments/assets/a7482c93-f0ff-4fdd-b755-9f9e0e6c9749" />

As you can see, permission was denied when trying to run `touch` to create a file as vini.

---
### Step 7: Sudo Privileges test.

Tried running commands that require administrative privileges as both of the new users. Confirmed sr-admin has full access and jr-admin has limited access.

<img width="1605" height="547" alt="Captura de tela 2026-09-28 173100" src="https://github.com/user-attachments/assets/afe7a831-20a3-4d75-8910-7e298067bdc4" />

As you can see, sr-admin can run apt update.

<img width="1572" height="867" alt="Captura de tela 2026-09-28 173652" src="https://github.com/user-attachments/assets/bb957529-467e-44b8-b9d9-94ecfad15144" />

jr-admin, on the other hand, cannot (Got a sorry message). However, they can still run systemctl restart, as specified in `/etc/sudoers`.

---
## Results:
Here is a list of commands demonstrating the current state of the sysadmins group and the sysadmin-shared directory:
 
 <img width="1562" height="861" alt="Captura de tela 2026-09-28 173921" src="https://github.com/user-attachments/assets/19fa1f5d-075e-4719-9698-0108dc2a4f9b" />

 As you can see, both sr-admin and jr-admin were also automatically added as users you can log in as in the starting screen:

 <img width="1919" height="960" alt="Captura de tela 2026-09-28 174144" src="https://github.com/user-attachments/assets/fb1897bd-1339-480d-8ca4-604312378099" />










