# Azure Active Directory Lab: Domain Services, Group Policy, and Access Management

This lab demonstrates the deployment and configuration of an Active Directory environment using Azure virtual machines. It includes setting up a domain controller, joining a client to the domain, configuring user roles and group policies, managing shared resources, and resolving RDP access issues—simulating a real-world IT environment.

---

## Lab Overview

- **Domain Controller (DC):** Windows Server 2022  
- **Client Machine:** Windows 10  
- **Environment:** Microsoft Azure Virtual Machines  

### Key Tasks

- Deployed VMs within a virtual network  
- Installed Active Directory Domain Services and DNS roles  
- Created domain users, groups, and organizational units (OUs)  
- Applied Group Policy Objects (GPOs)  
- Managed shared resources and permissions  
- Troubleshot user login and remote desktop connectivity  

---

## Step-by-Step Walkthrough with Screenshots

### 1. Creating Virtual Network and VMs  
![Screenshot 2025-05-29 214951](https://github.com/user-attachments/assets/38c025d1-68d9-4466-b689-36dc067b4ca4)  
![Screenshot 2025-05-29 220056](https://github.com/user-attachments/assets/6202fb73-0788-4828-8a0e-63919bbca709)  

**Steps:**  
- In Azure Portal, go to **Create a Resource > Networking > Virtual Network**.  
- Give the VNet a name, select the region, and define an address space.  
- Create a subnet for internal communication.  
- Then create two VMs: one running **Windows Server 2022** (for the DC), and the other running **Windows 10** (as a client).  
- Ensure both are on the same virtual network and subnet.

---

### 2. Installing Active Directory and DNS on the Domain Controller  
![Screenshot 2025-05-29 220331](https://github.com/user-attachments/assets/32b931d0-7c46-4377-ba3a-ef99c3c8ebf3)  
![Screenshot 2025-05-29 222200](https://github.com/user-attachments/assets/4acad46e-b727-4e64-bb7c-def875f6a708)  

**Steps:**  
- RDP into the Windows Server 2022 VM.  
- Open **Server Manager**, click **Manage > Add Roles and Features**.  
- Use a **Role-based or feature-based installation**.  
- Select the local server, and check **Active Directory Domain Services** and **DNS Server**.  
- After installation, click the yellow exclamation icon, then **Promote this server to a domain controller**.  
- Select **Add a new forest**, enter your domain name (lab.local), and proceed.  
- Set a Directory Services Restore Mode (DSRM) password.  
- Complete the wizard and restart the server when prompted.

---

### 3. Joining the Client Machine to the Domain  
![Screenshot 2025-05-31 130148](https://github.com/user-attachments/assets/ab1bc696-2b98-4aa4-a858-8b4954182d41)  

**How to configure:**  
- RDP into the Windows 10 client VM.  
- Go to **Network & Internet > Change adapter options**, right-click the NIC > **Properties** > **IPv4** settings.  
- Change the **DNS server** to the private IP address of the DC.  
- Then go to **System > About > Rename this PC (advanced)** > **Change settings**.  
- Click **Change**, select **Domain**, and enter your domain name (lab.local).  
- Authenticate with domain admin credentials.  
- Reboot when prompted to complete domain join.

---

### 4. Creating Organizational Units, Users, and Groups  
![Screenshot 2025-05-31 132742](https://github.com/user-attachments/assets/72eab8ce-cc87-4ffb-af1b-3716971c321f)  

**Steps:**  
- On the domain controller, open **Active Directory Users and Computers**.  
- Right-click your domain name > **New > Organizational Unit**, and name it ( `HR`, `IT`).  
- Within each OU, right-click > **New > User** to create user accounts.  
- Set usernames, passwords, and select whether to require password change on next login.  
- To create groups, right-click > **New > Group**, define scope and type, then add members through the **Members** tab.

---

### 5. Applying Group Policy for Desktop Wallpaper Enforcement  
![Screenshot 2025-05-31 140323](https://github.com/user-attachments/assets/522b8720-7da6-4909-a356-355a3144caba)  

**Steps:**  
- Open **Group Policy Management** on the DC.  
- Right-click on the OU with target users > **Create a GPO in this domain, and Link it here**.  
- Name it (Wallpaper Dekstop) and click **OK**.  
- Right-click the new GPO > **Edit**.  
- Navigate to:  
  `User Configuration > Policies > Administrative Templates > Desktop > Desktop > Desktop Wallpaper`  
- Set it to **Enabled**, and provide the UNC path to the image file.  
- Use `\\<ServerName>\<Share>` and ensure share/NTFS permissions allow read access.

---

### 6. Verifying Group Policy Application and User Login Behavior  
![Screenshot 2025-05-31 150330](https://github.com/user-attachments/assets/bd389de9-6bd6-4e83-8cac-79139a675f39)  
![Screenshot 2025-05-31 150736](https://github.com/user-attachments/assets/b5f22c86-643c-4475-893a-8ac1804882d3)  

**Steps:**   
- Log into the client with a domain user account.  
- Open Command Prompt and run: `gpresult /r`.  
- Verify the correct GPO is applied.  
- Confirm wallpaper, Task Manager restrictions, or other policy effects, you can do this by also attempting to open them to find  that the system will block that action.  

### 7. Troubleshooting Remote Desktop Access for Domain Users  
![Access Denied - RDP](https://github.com/user-attachments/assets/a39aedec-02db-4b9b-b297-7d42454df0a8)  

**Steps:**  
- Log into the client machine with a local admin or domain admin.  
- Go to **System Properties** > Remote tab > Select Users.  
- Click **Add**, then add `Domain Users` or the specific group needing RDP access.  
- Domain users should now be able to RDP into the VM.  

---

## Key Lessons Learned

- DNS is critical for domain joins and policy distribution.  
- Group Policy enables scalable configuration and restriction across user accounts.  
- Proper AD structuring (OUs, groups) makes management easier and cleaner.  
- RDP access requires appropriate local group membership, even in domain-joined setups.  
- Azure provides an accessible environment to replicate enterprise infrastructure.  

---

## Summary

This lab covered essential administrative and configuration tasks for managing a domain-based environment. The simulation of user and group management, policy enforcement, and access control troubleshooting in Azure reflects the responsibilities faced by IT support and system administrator roles in production networks.
