# Windows Server Active Directory Homelab

## Overview

This project documents my virtualized Windows Server Active Directory homelab, built to practice enterprise network administration and cybersecurity fundamentals.

The lab simulates a small business-style Windows domain environment using Windows Server 2025 Datacenter Evaluation and a Windows 11 client machine. The main focus of the project is to understand centralized identity management, domain authentication, Group Policy, file sharing, permissions, and basic account security in an enterprise-style network.

This homelab was created as a hands-on learning project to strengthen my practical skills in Windows Server administration, Active Directory, networking, and cybersecurity.

---

## Project Objectives

- Build a virtual Windows enterprise-style network
- Configure Windows Server as a Domain Controller
- Install and configure Active Directory Domain Services
- Create and manage Organizational Units, users, and groups
- Join a Windows 11 client machine to the domain
- Configure Group Policy Objects
- Set up SMB network file sharing
- Configure share permissions and NTFS permissions
- Map network drives using Group Policy
- Configure account lockout policies
- Test and verify domain authentication and policy application

---

## Lab Environment

- Server VM: Windows Server 2025 Datacenter Evaluation
- Server hostname: SYS1
- Server role: Domain Controller, DNS, and File Server
- Client VM: Windows 11 Pro
- Client role: Domain-joined client machine
- Virtualization platform: VMware Workstation
- Server RAM: 4 GB
- System type: 64-bit operating system, x64-based processor

---

## Tools and Technologies Used

- VMware Workstation
- Windows Server 2025 Datacenter Evaluation
- Windows 11 Pro
- Active Directory Domain Services
- Active Directory Users and Computers
- Group Policy Management Console
- DNS
- SMB File Sharing
- NTFS Permissions
- Command Prompt
- PowerShell

---

## Lab Setup Summary

The lab was created using virtualization software, with a Windows Server virtual machine acting as the main domain controller. A Windows 11 client virtual machine was then joined to the domain to test authentication, Group Policy, file sharing, and mapped drive configuration.

The server was configured with a static IP address to support reliable domain and DNS communication between the server and client.

---

## What I Configured

## 1. Windows Server Installation and Setup

I installed Windows Server 2025 Datacenter Evaluation in a virtual machine and completed the initial system configuration.

Tasks completed:

- Installed Windows Server 2025 Datacenter Evaluation
- Renamed or identified the server hostname
- Configured the server as a virtual machine in VMware Workstation
- Configured a static IP address
- Installed Active Directory Domain Services
- Promoted the server to a Domain Controller
- Configured the server to provide domain authentication and DNS services

---

## 2. Active Directory Domain Services

I configured Active Directory to create a centralized identity management environment.

Tasks completed:

- Created a new Active Directory domain
- Opened and used Active Directory Users and Computers
- Created Organizational Units to organize users, computers, and service accounts
- Structured the domain to represent a small enterprise environment

Example OU structure:

- Domain
  - Users
    - HR
    - IT
    - Accounting
  - Computers
  - Servers
  - Service Accounts

---

## 3. Organizational Units

Organizational Units were created to separate users, computers, departments, and administrative resources.

Purpose of OUs:

- Organize Active Directory objects
- Apply Group Policy to specific departments or systems
- Make user and computer management easier
- Reflect a realistic enterprise structure

Examples of OUs created:

- HR
- IT
- Accounting
- Computers
- Servers
- Service Accounts

---

## 4. User Account Management

I created multiple Active Directory user accounts for different departments.

Tasks completed:

- Created domain user accounts
- Assigned users to the correct department OUs
- Set user logon names
- Configured initial passwords
- Added user descriptions based on job roles
- Tested login using domain accounts on the client machine

Example users:

- John Doe: HR, Recruiter
- Jane Smith: IT, IT Support
- Alex Brown: Accounting, Accounts Assistant

---

## 5. Group Management

Security groups were created to manage permissions more efficiently.

Tasks completed:

- Created department-based security groups
- Added users to the correct groups
- Used groups to control access to shared resources
- Practiced group-based access control

Example groups:

- HR_Department: HR users
- IT_Department: IT users
- Accounting_Department: Accounting users

Using groups instead of assigning permissions directly to individual users makes administration easier and supports the principle of least privilege.

---

## 6. Windows Client Domain Join

A Windows 11 client virtual machine was joined to the domain to test the Active Directory environment.

Tasks completed:

- Configured the client DNS settings to point to the Domain Controller
- Joined the Windows 11 client to the Active Directory domain
- Restarted the client after domain join
- Logged in using domain user credentials
- Verified that domain authentication was working correctly

This helped me understand the importance of DNS in Active Directory environments.

---

## 7. Group Policy Objects

Group Policy Objects were created and linked to Organizational Units to manage users and computers centrally.

Tasks completed:

- Opened Group Policy Management Console
- Created new Group Policy Objects
- Linked GPOs to specific OUs
- Configured user and computer policy settings
- Applied policies to domain-joined clients
- Tested policy updates using gpupdate /force

Example GPOs configured:

- Password Policy: Enforce stronger password requirements
- Account Lockout Policy: Lock accounts after repeated failed login attempts
- Restrict Control Panel: Prevent standard users from accessing Control Panel
- Mapped Drive Policy: Automatically map shared network drives

---

## 8. Account Lockout Policy

I configured an account lockout policy to improve basic account security.

Purpose:

- Reduce the risk of brute-force login attempts
- Lock accounts after repeated failed login attempts
- Improve authentication security within the domain

Example settings:

- Account lockout threshold: 5 invalid attempts
- Account lockout duration: 15 minutes
- Reset account lockout counter after: 15 minutes

This helped me understand how account security policies can be enforced centrally using Group Policy.

---

## 9. File Sharing and Permissions

I configured a shared folder on the server to simulate a business file share.

Tasks completed:

- Created a shared folder on the server
- Enabled SMB sharing
- Configured share permissions
- Configured NTFS permissions
- Assigned access based on users and groups
- Tested access from the domain-joined client

Example shared folder:

- \\Sys1\shared

Permissions were configured using both share permissions and NTFS permissions. This helped me understand that effective access is determined by both layers.

---

## 10. Mapped Network Drives

I configured mapped network drives using Group Policy so that users automatically receive access to shared folders after logging in.

Tasks completed:

- Created a Group Policy Object for drive mapping
- Configured a mapped drive path
- Assigned a drive letter
- Linked the GPO to the correct User OU
- Refreshed Group Policy on the client
- Verified that the mapped drive appeared after login

Example mapped drive:

- Z: mapped to \\SERVER-NAME\SharedFiles

---

## Testing and Verification

To confirm that the lab was working correctly, I performed several tests from the domain-joined client machine.

Tests completed:

- Logged in using a domain user account
- Verified domain membership
- Confirmed that Group Policy Objects were applied
- Tested shared folder access
- Verified mapped network drive deployment
- Checked user group membership
- Confirmed account lockout policy behavior

Useful commands used:

- gpupdate /force
- gpresult /r
- whoami
- whoami /groups
- ipconfig /all

---

## Skills Demonstrated

This project helped me practice and demonstrate the following skills:

- Windows Server administration
- Active Directory configuration
- Domain Controller setup
- DNS configuration for Active Directory
- Organizational Unit management
- User and group management
- Group Policy creation and linking
- Domain client configuration
- SMB file sharing
- Share and NTFS permissions
- Mapped network drives
- Account lockout policies
- Basic identity and access management
- Troubleshooting domain connectivity
- Enterprise-style network administration

---

## Cybersecurity Relevance

This homelab is relevant to cybersecurity because Active Directory is widely used in enterprise environments and is a common target for attackers.

Through this project, I gained practical experience with:

- Identity and Access Management
- Authentication and authorization
- Least privilege access control
- Group-based permissions
- Centralized security policy enforcement
- Account lockout protection
- Domain-joined endpoint management
- File share access control
- Basic Windows enterprise security concepts

Understanding how Active Directory is configured and managed is important for both defensive and offensive cybersecurity roles.

---

## Challenges Faced

## DNS and Domain Joining

One challenge was understanding that the Windows client must use the Domain Controller as its DNS server before it can join the domain successfully.

If the DNS settings are incorrect, the client cannot locate the domain controller.

## Share Permissions vs NTFS Permissions

Another challenge was understanding the difference between share permissions and NTFS permissions.

I learned that share permissions control access over the network, while NTFS permissions control access at the file system level. The most restrictive permission usually applies.

## Group Policy Application

I also learned that Group Policy may not apply immediately. I used gpupdate /force and gpresult /r to refresh and verify applied policies.

---

## What I Learned

This project helped me understand how Windows enterprise environments are structured and managed.

I learned how Active Directory provides centralized control over users, computers, authentication, permissions, and policies. I also gained hands-on experience with Group Policy, file sharing, mapped drives, DNS configuration, and domain client management.

The project improved my confidence with Windows Server administration and gave me a better understanding of how identity and access management works in real organizations.

---

## Future Improvements

In the future, I would like to expand this homelab by adding:

- More Windows client machines
- A Kali Linux VM for controlled security testing
- Splunk or Wazuh for log monitoring
- Windows Event Forwarding
- PowerShell automation scripts
- More realistic departments and user accounts
- Backup and restore testing for Active Directory
- Additional Group Policy hardening
- Basic vulnerability scanning
- Security auditing of users, groups, and permissions
- Active Directory attack and defence practice in a safe lab environment

---

## Disclaimer

This project was created in a private virtual lab environment for educational purposes only. No real company systems, users, or production networks were involved.
