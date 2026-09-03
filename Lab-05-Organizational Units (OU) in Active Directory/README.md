Lab-05-Organizational Units (OU) in Active Directory

Objective

In this lab, we learn about Organizational Units (OUs) in Active Directory Domain Services (AD DS).

An OU is a container used to organize users, computers, groups, and other objects inside a domain.

Domain: homeLab.com

1. What is an Organizational Unit (OU)?

An Organizational Unit (OU) is a container in Active Directory used to organize objects based on departments, locations, or other requirements.

For example:

homeLab.com
│
├── Admin
├── HR
└── Finance

OUs make Active Directory easier to organize and manage.

2. OU and Groups

OU and Group are different and have different purposes.

OU

An OU is mainly used for:

Organizing Active Directory objects
Applying Group Policies (GPOs)
Delegating administrative permissions
Group

A Group is mainly used for:

Managing multiple users together
Assigning permissions
Controlling access to resources

In short:

OU → Organization and Administration
Group → Permissions and Access

3. Delegated Administration

Delegated administration means giving an administrator permission to manage a specific OU instead of giving them full Domain Administrator access.

Example:
homeLab.com
│
├── Admin
├── HR
└── Finance

An administrator could be given permission to manage only the HR OU.

This provides more controlled administration within the domain.

4. Creating an OU
Step 1

Open Server Manager.

Step 2

Go to:

Tools → Active Directory Users and Computers

You can also open it using:

dsa.msc
Step 3

Expand:

homeLab.com
Step 4

Right-click on homeLab.com.

Select:

New → Organizational Unit

Step 5

Create the following OUs:

Admin
HR
Finance

Click OK after creating each OU.

5. Creating an OU Inside Another OU

Active Directory allows us to create an OU inside another OU.

This creates a hierarchical structure and helps organize objects further.

Example:
homeLab.com
│
├── Admin
│   └── Admin Users
│
├── HR
│   └── HR Users
│
└── Finance
    └── Finance Users

Here:

Admin Users is inside the Admin OU.
HR Users is inside the HR OU.
Finance Users is inside the Finance OU.
How to create a sub-OU:
Right-click the Admin OU.
Select New → Organizational Unit.
Enter Admin Users.
Click OK.

Repeat the same process for:

HR → HR Users
Finance → Finance Users
6. Final OU Structure

After completing the lab:

homeLab.com
│
├── Admin
│   └── Admin Users
│
├── HR
│   └── HR Users
│
└── Finance
    └── Finance Users
	

7. Lab Summary

In this lab, we learned:

What an Organizational Unit (OU) is.
The purpose of OUs in Active Directory.
The difference between OU and Group.
How to create an OU.
How to create an OU inside another OU.
What Delegated Administration means.
How to organize a domain using department-based OUs.

