# Using-Group-Policy

# 🛡️ Assisted Lab: Using Group Policy

## 📌 Overview

This lab demonstrates how to use **Windows Group Policy Objects (GPOs)** to centrally manage and enforce security settings in an Active Directory environment. The lab covers creating Organizational Units (OUs), linking Group Policy Objects, configuring security policies, deploying logon/logoff scripts, and verifying that policies are successfully applied.

This project is based on a Windows Server 2019 domain environment and aligns with **CompTIA Security+ (SY0-701)** objectives. :contentReference[oaicite:0]{index=0}

---

## 🎯 Objectives

- Create and manage an Organizational Unit (OU)
- Move users and computers into the OU
- Create and link a Group Policy Object (GPO)
- Configure Account Lockout Policy
- Create folders using Group Policy Preferences
- Verify applied Group Policies using GPResult and RSOP
- Create and deploy logon and logoff scripts
- Test GPO deployment and script execution

---

## 🖥️ Lab Environment

| Component | Description |
|-----------|-------------|
| Domain Controller | Windows Server 2019 (DC10) |
| Client Machine | Windows Server 2019 (PC10) |
| Domain | ad.structureality.com |
| Directory Service | Active Directory |
| Management Tool | Group Policy Management Console (GPMC) |

:contentReference[oaicite:1]{index=1}

---

# 🔹 Part 1 – Create an Organizational Unit (OU)

Created a new Organizational Unit named:

```
SalesClients
```

Moved the following Active Directory objects into the OU:

- Dani (User)
- Cam (Administrator)
- PC10 (Computer)

This creates a dedicated container where security policies can be managed separately from the rest of the domain.

---

# 🔹 Part 2 – Create and Configure a Group Policy Object

Created a new Group Policy Object:

```
SalesPolicy
```

Linked the GPO to the **SalesClients** Organizational Unit.

Configured the following security settings:

### Account Lockout Policy

| Setting | Value |
|---------|-------|
| Account Lockout Threshold | 3 invalid logon attempts |

This helps protect against brute-force password attacks by locking an account after multiple failed login attempts.

---

# 🔹 Part 3 – Create Folder Using Group Policy Preferences

Configured a Group Policy Preference to automatically create the following folder on client computers:

```
C:\SalesDocs
```

This demonstrates how administrators can automatically deploy folders and other resources without manual configuration.

---

# 🔹 Part 4 – Verify Group Policy

Verified successful Group Policy deployment using:

- gpresult /r
- Resultant Set of Policy (RSOP)

Confirmed:

- SalesPolicy applied successfully
- User settings applied
- Computer settings applied (administrator account)
- Account Lockout Policy configured correctly
- SalesDocs folder created automatically

---

# 🔹 Part 5 – Create Logon and Logoff Scripts

Created a shared folder:

```
C:\scripts
```

Created two text files:

```
logon.txt
logoff.txt
```

Contents:

**logon.txt**

```
Hello, this is a logon script.
```

**logoff.txt**

```
Goodbye, this is a logoff script.
```

Created command files:

```
scriptlogon.cmd
scriptlogoff.cmd
```

Configured the scripts to reference shared network resources rather than local files.

---

# 🔹 Part 6 – Deploy Scripts with Group Policy

Configured the **SalesPolicy** GPO to execute:

### Logon Script

```
\\DC10\scripts\scriptlogon.cmd
```

### Logoff Script

```
\\DC10\scripts\scriptlogoff.cmd
```

Enabled:

- Display instructions in logoff scripts as they run

Restarted the client computer and verified that:

- Logon script executed successfully
- Logoff script executed successfully
- Script messages appeared during user logon and logoff

---

# 🛠️ Tools & Technologies

- Windows Server 2019
- Active Directory
- Group Policy Management Console (GPMC)
- Organizational Units (OU)
- Group Policy Objects (GPO)
- Group Policy Preferences
- GPResult
- Resultant Set of Policy (RSOP)
- Command Prompt
- Windows File Sharing

---

# 🔒 Security Concepts

- Active Directory Administration
- Centralized Policy Management
- Group Policy Objects (GPO)
- Organizational Units
- Account Lockout Policy
- Password Protection
- Least Privilege
- Security Baselines
- Windows Automation
- Logon Scripts
- Logoff Scripts
- Policy Enforcement
- Administrative Templates

---

# 📚 CompTIA Security+ Objectives

This lab aligns with:

- **4.5** – Modify enterprise capabilities to enhance security
- **4.7** – Explain the importance of automation and orchestration related to secure operations

:contentReference[oaicite:2]{index=2}

---

# ✅ Skills Demonstrated

- Active Directory administration
- Organizational Unit management
- Group Policy creation and deployment
- Windows security policy configuration
- Account lockout implementation
- Group Policy Preferences
- GPResult analysis
- RSOP troubleshooting
- Windows scripting
- Logon and logoff automation
- Network share configuration
- Enterprise Windows administration

---

# 📖 What I Learned

Through this lab, I learned how enterprise administrators use Group Policy to centrally manage Windows environments. I gained hands-on experience creating Organizational Units, deploying Group Policy Objects, enforcing security settings, automating user logon and logoff tasks with scripts, and verifying policy application using GPResult and RSOP. These skills are essential for securing and managing Windows-based enterprise networks.

---

## 👨‍💻 Author

**Bayram Guney**

Cybersecurity Student | CompTIA A+ | Network+ | Security+ | Security Operations | Active Directory | Windows Administration
