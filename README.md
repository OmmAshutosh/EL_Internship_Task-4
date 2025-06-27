# 🔥 Task 4: Setup and Use a Firewall on Windows/Linux

## 🎯 Objective  
Configure and test basic firewall rules to allow or block traffic, and understand how firewalls filter network connections.

---

## 🧰 Tools Used

- 🪟 **Windows Defender Firewall** – Built-in firewall on Windows  
- 🐧 **UFW (Uncomplicated Firewall)** – Simple firewall for Linux (Ubuntu/Debian)

> This guide covers practical steps for both Windows and Linux.

---

## 📋 Task Overview

| Step | Description                                    |
|------|------------------------------------------------|
| 1️⃣  | Open firewall configuration tool               |
| 2️⃣  | List current firewall rules                    |
| 3️⃣  | Block inbound traffic on port 23 (Telnet)      |
| 4️⃣  | Test firewall rule using local/remote tools    |
| 5️⃣  | Allow traffic on port 22 (SSH on Linux)        |
| 6️⃣  | Remove block rule and restore original state   |
| 7️⃣  | Document commands or steps taken               |
| 8️⃣  | Summarize how firewalls filter traffic         |


## 🪟 Windows Firewall – Steps

### ✅ Step 1: Open Firewall
- Go to: **Start → Windows Security → Firewall & network protection**
- Click **Advanced Settings** to open **Windows Defender Firewall with Advanced Security**


### ✅ Step 2: View Current Rules
- Navigate to **Inbound Rules** in the left pane.
- Scroll through existing rules to see active ports/services.


### ✅ Step 3: Block Port 23 (Telnet)
1. Click **"New Rule..."**
2. Select **Port → TCP → Specific port: 23**
3. Action: **Block the connection**
4. Apply to all profiles (Domain, Private, Public)
5. Name the rule `Block Telnet Port 23`


### ✅ Step 4: Test the Rule
- Use `telnet` or run an `nmap` scan from another system:
  ```bash
  nmap -p 23 <your Windows IP>

### ✅ Step 5: Remove the Rule
- Go back to Inbound Rules
- Right-click Block Telnet Port 23 → Delet
  ![image](https://github.com/OmmAshutosh/EL_Internship_Task-4/blob/main/rule_deletion.png)


## 🐧 Linux (UFW) – Steps

### ✅ Step 1: Enable UFW & View Rules
```bash
sudo ufw enable
sudo ufw status verbose
```

### ✅ Step 2: Block Port 23 (Telnet)
```bash
sudo ufw deny 23
```

### ✅ Step 3: Allow Port 22 (SSH)
```bash
sudo ufw allow 22
```

### ✅ Step 4: Test Rules
```bash
nmap -p 22,23 <your Linux IP>
```
- Expected:
  Port 22 = open
  Port 23 = closed/filtered

### ✅ Step 5: Remove Test Rule
```bash
sudo ufw delete deny 23
```
----------------------------------------------------------------------------------

## 🧠 How Firewalls Filter Traffic
Firewalls work by filtering incoming and outgoing traffic based on rules.
For example, by blocking Telnet (port 23), we prevent legacy insecure remote logins.
Allowing SSH (port 22) enables secure remote administration.

- Key Concepts:
    Ports = doors to services
    Rules = conditions to open or close them
    Profiles = context (Public, Private, Domain)

## 📚 References
```bash
- [Microsoft Firewall Docs]([url](https://nmap.org/))
- [UFW Manual]([url](https://help.ubuntu.com/community/UFW))
- [Nmap Port Scanner]([url](https://nmap.org/))

