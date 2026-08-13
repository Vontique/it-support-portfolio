# IT Support & Systems Administration Portfolio

Welcome to my technical portfolio. This repository documents an enterprise-grade IT infrastructure homelab, showcasing hands-on competencies in local systems administration, hybrid identity management, modern endpoint deployment, and ITSM incident resolution.

---

## 💼 Business Scenario
Our organization needed to secure remote workstations, enforce security compliance, and automate user onboarding without physical IT intervention. To achieve this, we designed and deployed a scalable hybrid infrastructure bridging on-premises Active Directory with cloud-based endpoint management.

---

## 🛠️ Technical Stack
* **Hypervisors & Virtualization:** Oracle VirtualBox / Hyper-V (Internal Networking)
* **Operating Systems:** Windows Server 2022, Windows 11 Pro (25H2), Windows 10 Pro (22H2)
* **Directory Services & Identity:** Active Directory Domain Services (AD DS), Microsoft Entra ID, Microsoft Entra Connect
* **Endpoint Management & ITSM:** Microsoft Intune, Windows Autopilot, Group Policy (GPO), Intune Connector for Active Directory
* **Automation:** PowerShell, CSV Batch Provisioning

---

## 🏗️ Lab Architecture Overview

### Phase 1: Local Infrastructure Build
* Deployed an isolated internal network using a hypervisor housing a Windows Server 2022 Domain Controller and a Windows client VM.
* Configured AD DS, DNS, and DHCP roles for the mock domain `manilacorp.local`.
* Structured organizational units (`PH_HQ_Users`, `IT_Dept`, `Sales_Dept`) and used a PowerShell script to bulk-import 20 mock users via CSV.
* Enforced security baselines, desktop configurations, and access restrictions through Group Policies (GPOs).

### Phase 2: Hybrid Identity Bridge (Entra ID)
* Activated a trial sandbox Microsoft 365 Business Premium tenant (`michaelabarintos20gmail.onmicrosoft.com`).
* Configured Microsoft Entra Connect on the local domain controller to bridge on-premises Active Directory objects with the cloud.
* Validated directory synchronization, ensuring PowerShell-provisioned local users replicated successfully to the Entra ID Admin Center.

### Phase 3: Modern Endpoint Management (Intune & Autopilot)
* Enabled automatic enrollment so synced cloud accounts register client VMs directly into Microsoft Intune.
* Deployed Compliance Policies (BitLocker, Windows Defender) and Configuration Profiles (restricted USB ports, unified corporate lock screens).
* Silently pushed essential software packages (Google Chrome, M365 Apps) during setup.
* Extracted hardware hashes via PowerShell, configured Autopilot deployment profiles, customized the OOBE sequence, and executed zero-touch provisioning.

---

## 🎫 Featured Incident Logs & Tickets

* **[INC-1042: Windows Autopilot ESP Timeout & Hybrid Join Resolution](./tickets/INC-1042.md)**
  * **Status:** Resolved ✅
  * **Summary:** Bypassed OOBE Enrollment Status Page provisioning timeouts (`0x800705b4`) via a Windows 11 25H2 build upgrade, resolved domain controller routing blocks, and verified full hybrid-joined status for client `sgomez`.
* **[INC-1043: Microsoft Entra ID Conditional Access Policy Enforcement & Verification](./tickets/INC-1043.md)**
  * **Status:** Resolved ✅
  * **Summary:** Enforced a network-based location restriction policy blocking unauthorized cloud access from untrusted locations, validated via Entra sign-in error logs (53003).
* **[INC-1044: Active Directory Account Lockout & Password Reset Resolution](./tickets/INC-1044.md)**
  * **Status:** Resolved ✅
  * **Summary:** Remediated a locked user account via ADUC, cleared lockout threshold flags, and executed a temporary password reset enforcing a mandatory change at next logon for client `sgomez`.
* **[INC-1045: Workstation IP Configuration & DHCP Lease Troubleshooting](./tickets/INC-1045.md)**
  * **Status:** Resolved ✅
  * **Summary:** Diagnosed and resolved an APIPA network drop (169.254.x.x) resulting from an unidentified network state, verified DHCP client service and gateway connectivity, and successfully restored full IP communication for client `sgomez`.
* **[INC-1055: Print Spooler Recovery & Remote Desktop Connectivity](./tickets/INC-1055.md)**
  * **Status:** Resolved ✅
  * **Summary:** Established a remote desktop connection to client `CLIENT08`, remediated a disabled Print Spooler service via `services.msc`, mapped network printer `PRINTER01` via the AD DC environment, and verified print queue restoration.
