# Active-Directory-Home-Lab
A hands-on Active Directory lab environment built on Windows Server 2022 and Hyper-V, featuring automated user management and group policy configuration via PowerShell.

## 🚀 Progress Tracking
- [x] Initial VM Creation & Hardware Configuration
- [x] OS Installation (Windows Server 2022 Standard)
- [x] Server Renaming & Static IP Configuration
- [ ] Active Directory Domain Services (AD DS) Installation
- [ ] Post-Promotion Domain Verification
- [ ] PowerShell Automation Script Execution

## 💻 System Specifications (Audited)
To ensure stability during the installation, the virtual environment was configured as follows:

| Component | Value | Documentation Note |
| :--- | :--- | :--- |
| **Virtualization** | Microsoft Hyper-V (Gen 2) | UEFI-based for modern OS support |
| **Operating System** | Windows Server 2022 | Desktop Experience (GUI) selected |
| **Memory (Startup)** | 2048 MB (2 GB) | Increased from 524 MB for installer stability |
| **Storage** | 49 GB VHDX | Thin-provisioned virtual storage |

## ⚠️ Troubleshooting & Lessons Learned
**The RAM Trap:** Attempting to boot the Windows Server 2022 installer with 524 MB of RAM (as suggested in some guides) caused the boot loader to fail. Increasing the startup RAM to **2 GB** was the critical fix.
**Boot Priority:** Corrected a "No boot image found" error by manually adjusting the **SCSI Controller** settings to prioritize the DVD/ISO drive over the unallocated hard disk.
**Hyper-V "Press Any Key":** Identified that the 2-second boot window requires immediate focus on the VM window to initiate the OS installer.

### 🔧 Detailed Hyper-V Configuration
To replicate this environment, ensure the following settings are applied in Hyper-V Manager:

**Generation:** Generation 2 (supports UEFI and Secure Boot).
**Security:** * **Secure Boot:** Enabled (Standard Windows template). *Note: Temporarily disabled during initial ISO boot troubleshooting.*
    * **TPM:** Enabled (Required for specific Windows Server security features).
**Processor:** 2 Virtual Processors (minimum recommended for Server 2022 GUI).
**Memory:** * Startup RAM: 2048 MB.
    * Dynamic Memory: Disabled (to ensure consistent performance during AD DS promotion).
**Storage:** * Controller: SCSI Controller.
    * Drive 0: 49GB VHDX (Dynamically expanding).
    * Drive 1: DVD Drive (Mapped to Windows Server 2022 ISO).
**Networking:** Connected to `Default Switch` (provides NAT/Internet access for updates).

## ⚙️ Post-Installation Configuration
Before promoting the server to a Domain Controller, I performed the following "Identity" configurations to ensure network stability:

**Server Renaming:** Successfully changed the default hostname to **`DC01`**. This ensures that all future Active Directory logs, certificates, and DNS records use a standardized, professional naming convention.
**Static IP Assignment:** Transitioned from DHCP to a static configuration to ensure the Domain Controller remains a persistent "Lighthouse" for the network.
     **IPv4 Address:** `172.20.112.111`
     **Subnet Mask:** `255.255.240.0`
     **Default Gateway:** `172.20.112.1`
**DNS Strategy:** Configured the Preferred DNS to the loopback address (**127.0.0.1**). This tells the server to prioritize its own local Active Directory database for name resolution once the AD DS role is active.
