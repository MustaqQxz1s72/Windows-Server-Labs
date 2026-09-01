Lab 03 – Install Windows 11 and Join Client PC to Domain

Objective

Install Windows 11 in VMware Workstation and join the client PC to the HomeLab.com Active Directory domain hosted by the Domain Controller.

1. Download Windows 11 ISO

Download the official Windows 11 ISO file to use as the installation media for the client virtual machine.

2. Create Windows 11 Virtual Machine

Open VMware Workstation → Create a New Virtual Machine.

Select the downloaded Windows 11 ISO.
Specify the virtual machine location.
Configure the required Windows credentials.
Keep the remaining settings at their default values unless specific lab requirements exist.
Click Finish and complete the Windows 11 installation.

The newly installed system will be used as the client PC (PC-1).

3. Configure Client IP and DNS

Before joining the domain, configure the client with a valid IP address and point its DNS server to the Domain Controller.

Open:

Run → ncpa.cpl → Ethernet → Properties → Internet Protocol Version 4 (IPv4)

Configure:

IP Address: An address in the same network as the Domain Controller
DNS Server: 10.0.0.1 — the Domain Controller's IP address

Important: The client must use the Domain Controller as its DNS server so it can locate the Active Directory domain and Domain Controller.

Note: Disable and re-enable the Ethernet adapter after changing the network configuration if required.

4. Join the Client PC to the Domain

Open:

Run → sysdm.cpl

Select Computer Name → Change.
Select Domain.
Enter: HomeLab.com
Click OK.
When prompted, enter domain administrator credentials.

Example:

Username: .\Administrator
Password: Domain Administrator password

After successful authentication, Windows confirms that the computer has joined the domain.

Restart the client PC when prompted.

5. Verify the Client in Active Directory

On the Domain Controller, open:

Server Manager → Tools → Active Directory Users and Computers

Navigate to:

HomeLab.com → Computers

The client computer PC-1 should appear in the Computers container.

This confirms that the Windows 11 client has successfully joined the HomeLab.com domain.

Key Concepts
Client PC

A computer that uses services and resources provided by a server, such as authentication, DNS, Group Policy, and shared resources.

Domain Join

The process of connecting a computer to an Active Directory domain so that it can be centrally managed and users can authenticate using domain accounts.

DNS in Active Directory

DNS allows domain clients to locate Domain Controllers and Active Directory services. Therefore, domain clients should normally use the Domain Controller's DNS server rather than an external DNS server.

Workgroup vs Domain

Workgroup:
Computers are managed independently using local accounts.

Domain:
Computers and users are centrally managed through Active Directory and Domain Controllers.

Why must the client use the Domain Controller's DNS?

Active Directory relies on DNS records to locate Domain Controllers and other domain services. If the client uses an incorrect DNS server, domain joining and domain authentication can fail.