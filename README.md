# Azure-Based Active Directory Deployment and Access Management Lab

This lab demonstrates the setup of a basic Active Directory environment using Windows Server and a domain-joined client. It includes user creation, Group Policy configuration, and troubleshooting access issues, simulating an internal business network.

---

## 📋 Lab Overview

- Windows Server 2022 as Domain Controller (DC)  
- Windows 10/11 VM as domain client  
- Tasks performed:  
  - Installed Active Directory and DNS roles on DC  
  - Created domain users, organizational units (OUs), and groups  
  - Applied Group Policies (wallpaper enforcement, Task Manager restriction, etc.)  
  - Shared files and managed permissions  
  - Troubleshot login and remote access errors  

---

## 🖼️ Screenshots and Explanations

### Creating VNET and VMs  
![Screenshot 2025-05-29 214951](https://github.com/user-attachments/assets/38c025d1-68d9-4466-b689-36dc067b4ca4) ![Screenshot 2025-05-29 220056](https://github.com/user-attachments/assets/6202fb73-0788-4828-8a0e-63919bbca709)  
> Created an Azure Virtual Network and deployed two Virtual Machines: one running Windows Server 2022 as the Domain Controller, and one Windows 10 client to join the domain.

### Installing AD and DNS on DC  
![Screenshot 2025-05-29 220331](https://github.com/user-attachments/assets/32b931d0-7c46-4377-ba3a-ef99c3c8ebf3) ![Screenshot 2025-05-29 222200](https://github.com/user-attachments/assets/4acad46e-b727-4e64-bb7c-def875f6a708)  
> Installed Active Directory Domain Services and DNS roles on the Windows Server VM to establish domain infrastructure.

### Joining Client PC to DC Domain  
![Screenshot 2025-05-31 130148](https://github.com/user-attachments/assets/ab1bc696-2b98-4aa4-a858-8b4954182d41)  
> Successfully joined the Windows 10 client machine to the newly created domain.

### Creating Users, OUs, and Groups  
![Screenshot 2025-05-31 132742](https://github.com/user-attachments/assets/72eab8ce-cc87-4ffb-af1b-3716971c321f)  
> Created Organizational Units (OUs), user accounts, and security groups to organize and manage domain resources effectively.

### Applying Group Policy for Desktop Wallpaper  
![Screenshot 2025-05-31 140323](https://github.com/user-attachments/assets/522b8720-7da6-4909-a356-355a3144caba)  
> Applied a Group Policy Object (GPO) to enforce a corporate desktop wallpaper on all domain-joined machines, demonstrating centralized configuration management.

### Verifying Policy Application and User Permissions  
![Screenshot 2025-05-31 150330](https://github.com/user-attachments/assets/bd389de9-6bd6-4e83-8cac-79139a675f39) ![Screenshot 2025-05-31 150736](https://github.com/user-attachments/assets/b5f22c86-643c-4475-893a-8ac1804882d3)  
> Logged in with domain user accounts to verify that Group Policies and permissions were correctly applied, such as enforced wallpaper and disabled Task Manager.

### RDP Access Troubleshooting  
![Access Denied - RDP](https://github.com/user-attachments/assets/a39aedec-02db-4b9b-b297-7d42454df0a8)  
> Encountered an error preventing domain users from remotely accessing the client VM via RDP. Resolved by accessing the Domain Controller, modifying the client VM’s system properties, and explicitly granting RDP permissions to the domain users group.

---

## 🧠 Lessons Learned

- Interaction and precedence of NTFS and share permissions  
- Importance of correct DNS configuration for domain authentication  
- Configuring “Allow log on locally” rights for users  
- Managing RDP access via system properties when Group Policy settings alone are insufficient  

---

## 🔍 Lab Purpose and Overview

This lab provides foundational experience in deploying and managing a Windows Active Directory domain environment within a cloud infrastructure using Microsoft Azure. It covers critical skills such as domain service installation, user and group management, Group Policy deployment, resource sharing, and troubleshooting access control challenges.

Such competencies are essential for entry-level IT roles including system administration, network support, and IT helpdesk functions. The lab simulates real-world scenarios, reinforcing knowledge necessary for maintaining secure, organized, and operational enterprise network environments.

---

## ✅ Final Thoughts

The lab reinforces practical skills in:  
- Building and configuring domain-based IT infrastructure in a cloud environment  
- Managing users, policies, and shared resources effectively  
- Diagnosing and resolving common access and connectivity issues  

