Lab 2 – Install AD DS and Promote Server to Domain Controller

Objective

Install the Active Directory Domain Services (AD DS) role on Windows Server and promote the server to the first Domain Controller (DC) in a new forest.

1. Local Users and Groups – Before Promotion

Open Run → compmgmt.msc → Local Users and Groups.

Before promotion, the server uses the local SAM (Security Account Manager) database to manage local accounts.

After promotion to a Domain Controller, authentication and account management are handled by Active Directory, so the traditional local user/group management is no longer available in the same way.

2. Storage – Before Promotion

Before installing AD DS, the NTDS and SYSVOL folders are not present.

These folders are created during domain controller promotion and contain important Active Directory data and domain configuration.

3. Server Configuration – Before Promotion

Review the server's current configuration before installing the AD DS role.

4. Configure a Static IP Address

Configure a static IP address before promoting the server.

1. IP Address: 10.0.0.1
2. Preferred DNS: 10.0.0.1

A Domain Controller requires reliable network and DNS configuration because Active Directory depends heavily on DNS.

Note: Disable and re-enable the Ethernet adapter after making network configuration changes if required.

5. Install AD DS Role

Go to:

Server Manager → Manage → Add Roles and Features

1. Select Role-based or feature-based installation.
2. Select the local server.
3. Select Active Directory Domain Services (AD DS).
4. Click Add Features.
5. Continue with the default features, including Group Policy Management.
6. Click Install.

6. Promote the Server

After installation, open the Server Manager notification flag and select:

Promote this server to a domain controller

Installing the AD DS role alone does not make the server a Domain Controller. The promotion process creates the domain and configures the server as a DC.

7. Create a New Forest

For the first Domain Controller:

1. Select Add a new forest
2. Root domain name: HomeLab.com

This creates a new Active Directory forest and the first domain within it.

8. Configure Domain Controller Options

Keep the default capabilities:

1. DNS Server
2. Global Catalog (GC)

Set a secure password for Directory Services Restore Mode (DSRM).

9. Configure AD DS Database Locations

Specify the locations for:

1. NTDS database
2. Log files
3. SYSVOL

For a basic lab, the default locations are sufficient.

10. Prerequisites Check and Installation

Windows Server performs a prerequisite check before promotion.

The check verifies that the server meets important requirements such as networking, DNS, required services, and system configuration.

Once the checks pass successfully, click Install.

The server will restart automatically after promotion.

11. Domain Administrator Login

After restarting, the login screen shows:

HOMELAB\Administrator

This indicates that the server is now a member of the HOMELAB domain and is functioning as a Domain Controller.

12. Verify Domain Controller Configuration

After promotion:

1. The previous WORKGROUP configuration is replaced by the domain.
2. Active Directory becomes responsible for domain authentication and management.
3. The server now has the NTDS and SYSVOL structures.
4. Domain accounts and groups can be managed through Active Directory tools such as Active Directory Users and Computers (ADUC).

---

 Key Concepts

--> Active Directory (AD)

A Microsoft directory service that centrally stores and manages users, computers, groups, policies, and other resources within a Windows domain environment.

--> Active Directory Domain Services (AD DS)

The Windows Server role that provides the core functionality for creating and managing an Active Directory domain.

--> Domain Controller (DC)

A Windows Server that hosts AD DS and authenticates users and computers while providing access to Active Directory services.

--> NTDS

NTDS.dit is the main Active Directory database. It stores directory information such as users, groups, computers, and other Active Directory objects.

--> SYSVOL

A shared folder on Domain Controllers that stores important domain files, including Group Policy templates and scripts, and is replicated between Domain Controllers.

--> Why are prerequisites required?

Prerequisite checks help ensure that the server has the required network, DNS, system, and configuration settings before becoming a Domain Controller. This reduces the risk of an incorrect or failed AD deployment.

--> What happens to Local Users and Groups?

Before promotion, the server uses the local SAM database for local accounts. After promotion, the server becomes a Domain Controller and uses Active Directory for domain authentication and management.

Important: Local accounts are not simply "deleted." On a Domain Controller, local SAM-based account management is no longer available in the normal Windows Server interface because the server's primary security authority is Active Directory.
