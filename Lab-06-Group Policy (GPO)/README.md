Lab-06-Group Policy (GPO)

Objective

The objective of this lab is to understand and configure Group Policy Objects (GPOs) in a Windows Server Active Directory environment.

In this lab, a GPO was created and linked to the HR Organizational Unit (OU). A user policy was configured and tested on a Windows 11 domain client.

Lab Environment
Component	Details
Server OS	Windows Server 2022
Client OS	Windows 11
Domain	yourdomain.local
Directory Service	Active Directory Domain Services
Policy Management	Group Policy Management
OUs Used	Admin, HR, Finance
Lab Structure
yourdomain.local
│
├── Admin
├── HR
└── Finance
Tasks Performed
1. Verified Organizational Units

Verified the Admin, HR, and Finance OUs created in Lab 5.

2. Opened Group Policy Management

Opened:

Server Manager
→ Tools
→ Group Policy Management

Verified the domain and available OUs.

3. Created a GPO

Created a new GPO named:

HR Desktop Policy

The GPO was linked directly to the HR OU.

4. Configured User Policy

Edited the HR Desktop Policy and configured:

User Configuration
→ Administrative Templates
→ Control Panel
→ Prohibit access to Control Panel and PC settings

The policy was set to:

Enabled

5. Updated Group Policy

On the Windows 11 domain client, executed:

gpupdate /force

The policy update completed successfully.


6. Verified Applied Policies

Executed:

gpresult /r

The output showed:

Applied Group Policy Objects
    HR Desktop Policy


7. Tested the Policy

Logged in using a user account located inside the HR OU.

The configured Control Panel restriction was successfully applied.


8. Tested Policy Scope

Tested with a user from another OU, such as Finance.

The HR-specific policy was not applied because the GPO was linked to the HR OU.

-->Key Concepts Learned
Group Policy Object (GPO)
Group Policy Management
GPO creation and linking
User Configuration
Computer Configuration
Administrative Templates
OU-based policy application
gpupdate /force
gpresult /r
GPO scope and testing
Basic GPO troubleshooting
Result

Successfully created and configured a Group Policy Object, linked it to the HR Organizational Unit, applied the policy to a Windows 11 domain client, and verified that the policy was correctly applied based on the user's OU membership.