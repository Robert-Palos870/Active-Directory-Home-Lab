# Active-Directory-Home-Lab
A hands-on Active Directory lab environment built on Windows Server 2022 and Hyper-V, featuring automated user management and group policy configuration via PowerShell.

## 🚀 Progress Tracking
- [x] Initial VM Creation & Hardware Configuration
- [x] OS Installation (Windows Server 2022 Standard)
- [ ] Server Renaming & Static IP Configuration
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
* **The RAM Trap:** Attempting to boot the Windows Server 2022 installer with 524 MB of RAM (as suggested in some guides) caused the boot loader to fail. Increasing the startup RAM to **2 GB** was the critical fix.
* **Boot Priority:** Corrected a "No boot image found" error by manually adjusting the **SCSI Controller** settings to prioritize the DVD/ISO drive over the unallocated hard disk.
* **Hyper-V "Press Any Key":** Identified that the 2-second boot window requires immediate focus on the VM window to initiate the OS installer.
