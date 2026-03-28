Active Directory Domain Services Home Lab
Overview
A fully functional Windows Server-based Active Directory environment built from scratch to simulate real enterprise IT administration. This lab demonstrates hands-on competency with domain infrastructure, user management, Group Policy, and access control — skills directly applicable to desktop support and sysadmin roles.
---
Skills Demonstrated
Windows Server administration
Active Directory Domain Services (AD DS)
Group Policy Object (GPO) configuration
Organizational Unit (OU) design and management
User and group provisioning
Access control and security policy enforcement
---
Lab Environment
Component	Details
Server OS	Windows Server (Domain Controller)
Client OS	Windows 10/11 (domain-joined workstation)
Platform	Virtualization (VirtualBox / VMware / Hyper-V)
Domain Name	`homelab.local`
---
What Was Built
1. Domain Controller Setup
Installed and configured Windows Server
Promoted the server to a Domain Controller using AD DS
Configured DNS to support the domain environment
Verified domain replication and health using `dcdiag`
2. Organizational Units (OUs)
Designed a logical OU structure mirroring a real company:
```
homelab.local
├── IT Department
│   ├── Admins
│   └── Help Desk
├── HR Department
├── Finance Department
└── Contractors
```
3. User Accounts & Security Groups
Created 10+ domain user accounts across departments
Assigned users to appropriate OUs and security groups
Set account expiration dates for contractor accounts
Enforced naming conventions (first.last@homelab.local)
4. Group Policy Objects (GPOs)
GPO	Scope	Purpose
Password Policy	Domain-wide	12-character minimum, complexity required, 90-day expiry
Account Lockout	Domain-wide	Lock after 5 failed attempts, 30-minute lockout
Desktop Restrictions	Standard Users OU	Disable Control Panel, restrict USB drives
Screensaver Lock	All Users	Auto-lock after 10 minutes of inactivity
Software Restriction	Contractors OU	Block unapproved application execution
5. Real-World Admin Tasks Practiced
User provisioning: Creating new accounts, setting initial passwords, forcing password change at first login
Access control: Adding/removing users from groups to grant or revoke access to shared resources
Account management: Disabling terminated user accounts, unlocking locked accounts
GPO troubleshooting: Running `gpupdate /force` and `gpresult /r` to verify policy application
Password resets: Resetting domain passwords through Active Directory Users and Computers (ADUC)
---
Key Commands Used
```powershell
# Check domain controller health
dcdiag /test:replications

# Force Group Policy update on client
gpupdate /force

# Check applied Group Policy on a user
gpresult /r /user username

# Unlock a locked-out user account
Unlock-ADAccount -Identity "jsmith"

# Reset a user password
Set-ADAccountPassword -Identity "jsmith" -Reset -NewPassword (ConvertTo-SecureString "NewP@ssw0rd!" -AsPlainText -Force)

# List all users in an OU
Get-ADUser -Filter * -SearchBase "OU=IT Department,DC=homelab,DC=local"

# Disable a user account (offboarding)
Disable-ADAccount -Identity "jsmith"
```
---
What I Learned
How to stand up a Windows Server domain from scratch, including the full AD DS installation and promotion process
The real-world impact of GPO inheritance and how policies flow from domain → OU → object
How enterprises use OUs and groups to separate administrative scope
How to troubleshoot GPO application failures using `gpresult` and Event Viewer
The importance of the principle of least privilege when designing security groups
---
Relevance to IT Support / Desktop Support Roles
This lab directly mirrors what a tier-1 or tier-2 help desk technician encounters daily:
Password resets and account unlocks
User provisioning when a new employee joins
Access requests (adding users to groups)
Investigating why a policy isn't applying to a machine
Offboarding (disabling accounts on employee departure)
---
Screenshots / Documentation
> See the `/docs` folder for annotated screenshots of the lab environment, OU structure, and GPO configurations.
---
Lab Status
Active and ongoing — additional configurations and scenarios are added regularly.
