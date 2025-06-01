# Entry-Level-IT-Environment-in-Azure-Domain-Services-and-Support-Tools
This lab demonstrates the setup of a basic Active Directory environment using Windows Server and a domain-joined client. It includes user creation, Group Policy configuration, and resolving troubleshooting issues. Simulating internal business network.

---

## 📋 Lab Overview

- Windows Server 2022 as Domain Controller (DC)
- Windows 10/11 VM as domain client
- Tasks performed:
  - Installed AD and DNS on DC
  - Created domain users/groups
  - Applied group policies (wallpaper, Task Manager lock, etc.)
  - Shared files and managed permissions
  - Troubleshot login and path errors
    

---

## 🖼️ Screenshots

### Creating VNET and VMs
![Screenshot 2025-05-29 214951](https://github.com/user-attachments/assets/38c025d1-68d9-4466-b689-36dc067b4ca4) ![Screenshot 2025-05-29 220056](https://github.com/user-attachments/assets/6202fb73-0788-4828-8a0e-63919bbca709)
### Installing AD and DNS on DC
![Screenshot 2025-05-29 220331](https://github.com/user-attachments/assets/32b931d0-7c46-4377-ba3a-ef99c3c8ebf3) ![Screenshot 2025-05-29 222200](https://github.com/user-attachments/assets/4acad46e-b727-4e64-bb7c-def875f6a708)
### Joining Client PC to DC domain
![Screenshot 2025-05-31 130148](https://github.com/user-attachments/assets/ab1bc696-2b98-4aa4-a858-8b4954182d41)
### ✅ Creating Users, OU, and Groups
![Screenshot 2025-05-31 132742](https://github.com/user-attachments/assets/72eab8ce-cc87-4ffb-af1b-3716971c321f)
### 🎨 GPO for Desktop Wallpaper
![Screenshot 2025-05-31 140323](https://github.com/user-attachments/assets/522b8720-7da6-4909-a356-355a3144caba)
### Logging in as Created User and verifying that policies and permissions are properly configured
![Screenshot 2025-05-31 150330](https://github.com/user-attachments/assets/bd389de9-6bd6-4e83-8cac-79139a675f39) ![Screenshot 2025-05-31 150736](https://github.com/user-attachments/assets/b5f22c86-643c-4475-893a-8ac1804882d3)
### 🛠️ Error 0x3 Troubleshooting
![Screenshot 2025-05-31 145804](https://github.com/user-attachments/assets/a39aedec-02db-4b9b-b297-7d42454df0a8)

---

## 🧠 Lessons Learned

- How NTFS and share permissions interact
- Importance of DNS settings for domain login
- How to configure “Allow log on locally”

## 🌐 DNS Troubleshooting in Active Directory Lab
- Ran into DNS issues where domain-joined client machines would not resolve domain name
  
## 🧩 Problem Symptoms

- Client PC could not log into the domain
- Error when running `\\DC-1\SYSVOL`
- `ping DC-1` failed or returned incorrect IP
- Group Policy (`gpupdate /force`) failed to connect

## 🛠️ Resolution Steps
- Double checked DNS was properly configured
- Checked Firewall configurations
- Assigned VNET settings for VM and set custom Private IP Address for Client PC

## 🧠 Lessons Learned
- DNS issues cause the cascading of other issues
- Increased familiarity with DNS and back-end configuration
