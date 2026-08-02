# IT Support & Systems Administration Portfolio

Welcome to my technical portfolio. This repository documents an enterprise-grade IT infrastructure homelab, showcasing hands-on competencies in local systems administration, hybrid identity management, modern endpoint deployment, and ITSM incident resolution.

---

## 🏗️ Lab Architecture Overview

This portfolio simulates a complete corporate IT lifecycle—from on-premises infrastructure setup to cloud integration and automated endpoint management.

### Phase 1: Local Infrastructure Build (TESDA NC II Level)
* **Core Setup:** Deployed an isolated internal network using a hypervisor housing a Windows Server 2022 Domain Controller and a Windows client VM.
* **Active Directory (AD DS):** Configured AD DS, DNS, and DHCP roles for the mock domain `manilacorp.local`.
* **Automation & OUs:** Structured organizational units (`PH_HQ_Users`, `IT_Dept`, `Sales_Dept`) and used a PowerShell script to bulk-import 20 mock users via CSV.
* **Group Policies (GPOs):** Enforced security baselines, desktop configurations, and access restrictions.

### Phase 2: The Hybrid Identity Bridge (Entra ID Level)
* **Cloud Tenant:** Activated a sandbox Microsoft 365 Enterprise tenant (`manilacorp.onmicrosoft.com`).
* **Entra Connect:** Configured Microsoft Entra Connect on the local domain controller to bridge on-premises Active Directory objects with the cloud.
* **Verification:** Validated directory synchronization, ensuring PowerShell-provisioned local users replicated successfully to the Entra ID Admin Center.

### Phase 3: Modern Endpoint Management (Intune & Autopilot)
* **MDM Enrollment:** Enabled automatic enrollment so synced cloud accounts register client VMs directly into Microsoft Intune.
* **Security & Compliance:** Deployed Compliance Policies (BitLocker, Windows Defender) and Configuration Profiles (restricted USB ports, unified corporate lock screens).
* **App Packaging:** Silently pushed essential software packages (Google Chrome, M365 Apps) during setup.
* **Windows Autopilot:** Extracted hardware hashes via PowerShell, configured Autopilot deployment profiles, customized the OOBE sequence, and executed zero-touch provisioning.

---

## 🎫 Featured Incident Logs & Tickets

* **[INC-1042: Windows Autopilot ESP Timeout & Hybrid Join Resolution](./tickets/INC-1042.md)**
  * **Status:** Resolved ✅
  * **Summary:** Bypassed OOBE Enrollment Status Page provisioning timeouts (`0x800705b4`) via a Windows 11 25H2 build upgrade, resolved domain controller routing blocks, and verified full hybrid-joined status for client `sgomez`.

---

## 🛠️ Core Tech Stack & Tools
* **Operating Systems:** Windows Server 2022, Windows 11 Enterprise (25H2)
* **Virtualization:** Oracle VirtualBox / Hyper-V (Internal Networking)
* **Directory Services:** Active Directory Domain Services (AD DS), Microsoft Entra ID, Entra Connect
* **Endpoint Management:** Microsoft Intune, Windows Autopilot, Group Policy (GPO)
* **Automation:** PowerShell, CSV Batch Provisioning
