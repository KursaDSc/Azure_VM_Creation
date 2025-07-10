🎓 Virtual Machine Deployment Report on Microsoft Azure
Student Name: Kürşad Selicioğlu
Assignment Title: Windows Virtual Machine Deployment
Date: July 7, 2025

📌 1. Objective
The aim of this assignment is to practice deploying and configuring a virtual machine (VM) using the Microsoft Azure portal. A Windows Server-based virtual machine was created to explore key Azure components and understand the basics of cloud infrastructure.

🧩 2. Technologies and Components Used
Component	Description
Cloud Platform	Microsoft Azure
Operating System	Windows Server 2019 Datacenter
VM Size	Standard B1s (1 vCPU, 1 GiB RAM)
Region	West Europe
Resource Group	StudentKursadSelicioglu_RG
Storage Type	StorageV2 (RA-GRS)
Disk Type	SCSI (OS Disk)
IP Configuration	Both Public and Private IP assigned
DNS Name	Not configured
VM Generation	Generation 2
Virtual Network	StudentKursadSelicioglu-VM-vnet
Auto Shutdown	Disabled
Security Features	Secure Boot, Trusted Launch, vTPM enabled
Provisioning Status	Successful
Created At	July 7, 2025 – 08:44 UTC

🔧 3. Provisioned Resources
a. Virtual Machine
Computer Name: StudentKursadSe

Operating System: Windows Server 2019

vCPU: 1

RAM: 1 GiB

Status: Running

Agent Status: Ready

📸 Screenshot: Azure portal – Virtual Machine Overview Page

b. Resource Group
Name: StudentKursadSelicioglu_RG

Region: West Europe

📸 Screenshot: Resource Group Overview Page

c. Storage Account
Name: kursad

Redundancy: Geo-redundant Storage (GRS)

Access Tier: Hot

Performance Tier: Standard

Large File Share: Enabled

📸 Screenshot: Storage Account – Configuration Overview

d. Virtual Network (VNet)
Name: StudentKursadSelicioglu-VM-vnet

Subnet: default

Private IP: Automatically assigned

Public IP: Assigned (IP address is hidden for security)

📸 Screenshot: VM Network Interface (NIC) Page

🛡️ 4. Security Configuration
Secure Boot: Enabled

vTPM: Enabled

Integrity Monitoring: Disabled

Monitoring & Diagnostics: Not configured

📸 Screenshot: VM > Security Tab

📤 5. Backup & Snapshots
Number of Snapshots: 2

Soft Delete Retention: 14 days

Last Snapshot Update: July 8, 2025

📸 Screenshot: Storage Account > Backup (Snapshot) Tab

⚙️ 6. Optional Tasks on the Virtual Machine
Optional tasks were performed to test extended functionality and VM usability, including web publishing, SQL Server configuration, and Azure File Share usage.

✅ 6.1 Install IIS and Publish a Website
IIS Web Server role was installed via Server Manager > Add Roles and Features.

A basic index.html page was placed under C:\inetpub\wwwroot\.

Default port 80 was already open in the NSG.

The site was accessed via browser using the VM's public IP.

📸 Screenshot: IIS Welcome Page + Custom HTML Page Displayed in Browser

✅ 6.2 Install SQL Server Express and Create a Database
SQL Server Express 2019 installed with default settings.

Connected using SQL Server Management Studio (SSMS) at localhost\SQLEXPRESS.

A database named TestDB was created.

Sample table creation and data insert/query operations were tested.

📸 Screenshot: SSMS showing TestDB and sample SQL query execution

✅ 6.3 Azure File Share Operations
Azure File Share created in the existing storage account.

The share was mounted to the VM using the following command:

powershell
Kopyala
Düzenle
net use Z: \\<storageaccount>.file.core.windows.net\<sharename> /user:Azure\<storageaccount> <storage-key>
Files were created, read, and deleted using PowerShell and File Explorer.

📸 Screenshot: Mounted File Share in File Explorer with sample files

🧠 Reflections
This section helped reinforce practical knowledge of using a Windows VM in a cloud environment. Key takeaways include:

IIS setup is straightforward and publicly accessible via Azure NSG rules.

SQL Server Express provides a lightweight testing environment.

Azure File Shares offer reliable cloud-integrated file storage with easy mounting.

📝 7. Conclusion & Evaluation
This assignment provided hands-on experience with deploying a Windows-based virtual machine on Azure. Key learning points:

Understanding the relationship between Resource Groups, VMs, Virtual Networks, and Storage Accounts

Familiarity with Azure’s VM creation wizard

Initial security configuration (Secure Boot, vTPM)

Optional VM tasks like web publishing and file share integration

💡 Recommendations for Future Work
Enable full monitoring and diagnostics (Azure Monitor, Log Analytics)

Automate resource deployment using PowerShell or Azure CLI

Implement scheduled snapshot-based backup routines

🔗 8. References
Azure Virtual Machines Documentation

Azure Storage Accounts Overview

Azure Virtual Network Documentation

🖼️ 9. List of Screenshots (Appendix)
VM Overview Page

Resource Group Overview

Storage Account Configuration

Virtual Network Settings

Security Tab

Backup/Snapshot Tab

IIS Test Page

SSMS with TestDB

File Explorer with Azure File Share