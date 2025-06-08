# Azure Active Directory Lab: Domain Services, Group Policy, and Access Management

This lab demonstrates the deployment and configuration of an Active Directory environment using Azure virtual machines. It includes setting up a domain controller, joining a client to the domain, configuring user roles and group policies, managing shared resources, and resolving RDP access issues—simulating a real-world IT environment.

---

## Lab Overview

- Domain Controller (DC): Windows Server 2022  
- Client Machine: Windows 10  
- Environment: Microsoft Azure Virtual Machines  

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
A virtual network was created in Azure to allow communication between the two VMs. One VM was configured to run Windows Server 2022 as the domain controller. The second VM was provisioned with Windows 10 to act as a domain-joined client.

---

### 2. Installing Active Directory and DNS on the Domain Controller  
![Screenshot 2025-05-29 220331](https://github.com/user-attachments/assets/32b931d0-7c46-4377-ba3a-ef99c3c8ebf3)  
![Screenshot 2025-05-29 222200](https://github.com/user-attachments/assets/4acad46e-b727-4e64-bb7c-def875f6a708)  
Active Directory Domain Services (AD DS) and DNS roles were installed using Server Manager. The server was then promoted to a domain controller and a new forest and domain were configured.

---

### 3. Joining the Client Machine to the Domain  
![Screenshot 2025-05-31 130148](https://github.com/user-attachments/assets/ab1bc696-2b98-4aa4-a858-8b4954182d41)  
The client machine’s DNS settings were configured to use the private IP of the domain controller. The system was then joined to the domain through the System Properties interface and successfully authenticated with the newly created domain.

---

### 4. Creating Organizational Units, Users, and Groups  
![Screenshot 2025-05-31 132742](https://github.com/user-attachments/assets/72eab8ce-cc87-4ffb-af1b-3716971c321f)  
Using Active Directory Users and Computers (ADUC), several organizational units (OUs) were created to logically organize domain objects. Domain users and security groups were added and placed in the appropriate OUs for management and policy control.

---

### 5. Applying Group Policy for Desktop Wallpaper Enforcement  
![Screenshot 2025-05-31 140323](https://github.com/user-attachments/assets/522b8720-7da6-4909-a356-355a3144caba)  
A Group Policy Object (GPO) was created and linked to the user OU to enforce a standardized desktop wallpaper. This GPO demonstrated centralized configuration deployment across domain-joined machines.

---

### 6. Verifying Group Policy Application and User Login Behavior  
![Screenshot 2025-05-31 150330](https://github.com/user-attachments/assets/bd389de9-6bd6-4e83-8cac-79139a675f39)  
![Screenshot 2025-05-31 150736](https://github.com/user-attachments/assets/b5f22c86-643c-4475-893a-8ac1804882d3)  
Domain users logged in to the client machine. Group Policies were verified—wallpaper enforcement and Task Manager restrictions were successfully applied, validating that the GPOs were functioning as expected.

---

### 7. Troubleshooting Remote Desktop Access for Domain Users  
![Access Denied - RDP](https://github.com/user-attachments/assets/a39aedec-02db-4b9b-b297-7d42454df0a8)  
Domain users initially encountered access denied errors when attempting to RDP into the client VM. The issue was resolved by remotely accessing the client system from the domain controller and manually adding the appropriate domain group to the local “Remote Desktop Users” group. This demonstrated how local permissions and group membership can impact domain-based access.

---

## Key Lessons Learned

- DNS configuration is critical for domain authentication and communication.  
- Active Directory and Group Policy provide scalable control of users, resources, and security settings.  
- NTFS and share-level permissions must be configured properly to ensure correct access control.  
- Remote Desktop access may require manual configuration outside of standard GPO deployment.  
- Cloud platforms like Azure offer flexible environments to simulate real-world IT infrastructure and troubleshoot common enterprise issues.

---

## Summary

This lab covered essential administrative and configuration tasks for managing a domain-based environment. The simulation of user and group management, policy enforcement, and access control troubleshooting in Azure reflects the responsibilities faced by IT support and system administrator roles in production networks.
