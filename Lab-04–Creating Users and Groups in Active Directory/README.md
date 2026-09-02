Lab-04–Creating Users and Groups in Active Directory

Objective

Create and manage domain users and groups in Active Directory Domain Services (AD DS), and understand how groups are used for centralized access and permission management.

Part 1 – Users
Types of Users in a Client OS

A Windows client operating system can have different types of local accounts:

1. Administrator

Has elevated privileges and can perform most administrative tasks on the local computer.

2. Standard User

Has limited permissions and is intended for normal day-to-day activities.

3. Guest

A restricted account intended for temporary or limited access. It is disabled by default on modern Windows versions.

To view local users:

Run → compmgmt.msc → Local Users and Groups → Users

Note: These are local accounts and are managed by the local computer's SAM database.

Users in an Active Directory Domain

In a domain environment, the main account types used for authentication are:

Domain User

A user account stored in Active Directory that can authenticate to domain-joined computers and access authorized domain resources.

Domain Administrator

A highly privileged administrative account used to manage the Active Directory environment and domain resources.

Creating a User in AD DS

1. Open Active Directory Users and Computers

On the Domain Controller:

Server Manager → Tools → Active Directory Users and Computers

Navigate to:

HomeLab.com → Users

Right-click Users → New → User.

2. Enter User Information

Enter the required information:

First Name
Last Name
Full Name
User Logon Name

Click Next and configure the user's password.

3. Configure Password Options

When creating a user, the following options are available:

User must change password at next logon – Forces the user to create a new password during the first login.
User cannot change password – Prevents the user from changing the password.
Password never expires – Prevents the password from expiring according to the normal domain password policy.
Account is disabled – Creates the account in a disabled state.

Select the appropriate options according to the organization's security requirements.

Click Next → Finish.

The domain user User1 is now created successfully.

4. Test the Domain User

On the Windows 11 client PC configured in Lab 3, sign out and log in using the newly created domain account.

Example:

HOMELAB\User1

5. Verify the Logged-In User

Open Command Prompt and run:

whoami

The output should identify the current domain and username, for example:

homelab\user1

This confirms that the client is authenticating the user through the HomeLab.com domain.

Part 2 – Groups
Why Use Groups?

Imagine HomeLab.com has several departments:

Accounts
HR
Administration
IT

Instead of assigning permissions to individual users one by one, users can be placed into groups.

For example:

HR Group → HR Users → HR Resources

Permissions can then be assigned to the group rather than to every individual user.

This makes access management easier, more consistent, and scalable.

Group Scope

Active Directory provides three main group scopes:

1. Domain Local

Primarily used to assign permissions to resources within the domain.

2. Global

Typically used to group users with similar roles or responsibilities from the same domain.

3. Universal

Can contain users and groups from multiple domains and is useful in multi-domain environments.

A common best-practice model is:

AGDLP

Accounts → Global Groups → Domain Local Groups → Permissions

Group Types
1. Security Group

Used to assign permissions to resources such as:

Shared folders
Files
Printers
Applications

Security groups have a Security Identifier (SID) and can be used in access control.

2. Distribution Group

Used primarily for email distribution and communication.

Distribution groups are not normally used for assigning Windows resource permissions.

Creating a Group in AD DS
1. Create a New Group

Open:

Active Directory Users and Computers → HomeLab.com → Users

Right-click Users → New → Group.

2. Configure the Group

Enter:

Group Name: HR
Group Scope: Select the required scope
Group Type: Security

Click OK.

The HR Security Group is now created.

3. Add Users to the Group

Open the HR group → Members → Add.

Enter the user's name, for example:

User2

Click Check Names → OK → Apply → OK.

4. Verify Group Membership

Open the HR group and select the Members tab.

You should see User2 listed as a member.

This confirms that the user has been successfully added to the HR group.

Key Concepts
User

An identity used to authenticate a person and provide access to authorized resources.

Group

A collection of users or other objects used to simplify administration and permission management.

Security Group

A group that can be used to assign permissions to Windows and Active Directory resources.

Distribution Group

A group primarily used for distributing email messages to multiple recipients.

Group Scope

Defines where a group can be used and which objects it can contain.

SID

A Security Identifier (SID) is a unique identifier assigned to security principals such as users and security groups. Windows uses SIDs when evaluating permissions.

Principle of Least Privilege

Users should receive only the permissions required to perform their job, reducing security risks and accidental access.