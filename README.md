🎓 Virtual Machine Deployment Report on Microsoft Azure  
Student Name: Kürşad Selicioğlu  
Assignment Title: Windows Virtual Machine Deployment  
Date: July 7, 2025  

📌 1. Objective  
The aim of this assignment is to practice deploying and configuring a virtual machine (VM) using the Microsoft Azure portal. A Windows Server-based virtual machine was created to explore key Azure components and understand the basics of cloud infrastructure.

🧩 2. Technologies and Components Used  
| Component         | Description                        |
|------------------|------------------------------------|
| Cloud Platform    | Microsoft Azure                   |
| Operating System  | Windows Server 2019 Datacenter    |
| VM Size           | Standard B1s (1 vCPU, 1 GiB RAM)  |
| Region            | West Europe                       |
| Resource Group    | StudentKursadSelicioglu_RG        |
| Storage Type      | StorageV2 (RA-GRS)                |
| Disk Type         | SCSI (OS Disk)                    |
| IP Configuration  | Both Public and Private IP        |
| DNS Name          | Not configured                    |
| VM Generation     | Generation 2                      |
| Virtual Network   | StudentKursadSelicioglu-VM-vnet   |   
| Auto Shutdown     | Disabled                          |
| Security Features | Secure Boot, Trusted Launch, vTPM |
| Provisioning Status | Successful                      |
| Created At        | July 7, 2025 – 08:44 UTC          |

🔧 3. Provisioned Resources  

**a. Virtual Machine**  
- Computer Name: StudentKursadSe  
- Operating System: Windows Server 2019  
- vCPU: 1  
- RAM: 1 GiB  
- Status: Running  
- Agent Status: Ready  

📸 [Screenshot: Azure portal – Virtual Machine Overview Page](./vm-overview.png)


**b. Resource Group**  
- Name: StudentKursadSelicioglu_RG  
- Region: West Europe  

📸 [Screenshot: Resource Group Overview Page](./resource-group-overview.png)


**c. Storage Account**  
- Name: kursad  
- Redundancy: Geo-redundant Storage (GRS)  
- Access Tier: Hot  
- Performance Tier: Standard  
- Large File Share: Enabled  

📸 [Screenshot: Storage Account – Configuration Overview](./storage-account-configuration.png)


**d. Virtual Network (VNet)**  
- Name: StudentKursadSelicioglu-VM-vnet  
- Subnet: default  
- Private IP: Automatically assigned  
- Public IP: Assigned (IP address is hidden for security)  

📸 [Screenshot: Virtual Network Overview Page](./vn-overview.png)


**e. Azure File Share Operations

Azure File Share was created in the existing storage account (kursad).

The share was mounted to the VM using PowerShell with storage account key authentication.

Because port 445 (SMB) is often blocked by ISPs or organizations, a test was first performed using the Test-NetConnection cmdlet to ensure accessibility.

Then, the credentials were stored securely with cmdkey and the share was persistently mounted using New-PSDrive.

📄 PowerShell Script Used:

        $connectTestResult = Test-NetConnection -ComputerName kursad.file.core.windows.net -Port 445
        if ($connectTestResult.TcpTestSucceeded) {
            cmd.exe /C "cmdkey /add:`"kursad.file.core.windows.net`" /user:`"localhost\kursad`" /pass:`"your-storage-key-here`""
            New-PSDrive -Name Z -PSProvider FileSystem -Root "\\kursad.file.core.windows.net\fileshare" -Persist
        } else {
            Write-Error -Message "Unable to reach the Azure storage account via port 445. Check to make sure your organization or ISP is not blocking port 445, or use Azure VPN or ExpressRoute."
        }

🔐 Note:

This approach is recommended for administrative access.

Mounting with Microsoft Entra or AD identity is preferred in production for least-privilege scenarios.

This script ensures that the share will reconnect automatically after reboot.

📸 [Screenshot: Mounted File Share in File Explorer](./fs-mounted.png)
📸 [Screenshot: Azure File Share Overview Page](./st-fileshare.png)


📝 4. Conclusion & Evaluation
    This assignment provided hands-on experience with deploying a Windows-based virtual machine on Azure. Key learning points:

    Understanding the relationship between Resource Groups, VMs, Virtual Networks, and Storage Accounts

    Familiarity with Azure’s VM creation wizard

    Optional VM tasks like web publishing and file share integration


💡 Recommendations for Future Work

    Enable full monitoring and diagnostics (Azure Monitor, Log Analytics)

    Automate resource deployment using PowerShell or Azure CLI

    Implement scheduled snapshot-based backup routines


🔗 8. References

    Azure Virtual Machines Documentation

    Azure Storage Accounts Overview

    Azure Virtual Network Documentation