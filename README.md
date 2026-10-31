<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory logo"/>
</p>

<h1>On-Premises Active Directory Deployed in the Cloud (Azure)</h1>

This lab deploys an on-premises style Active Directory environment in Microsoft Azure: a Windows Server domain controller and a Windows 10 client, with organizational units, an admin account, a domain-joined client, and bulk user creation through PowerShell.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used</h2>

- Windows Server 2022 (Domain Controller: DC-1)
- Windows 10 21H2 (Client: Client-1)

<h2>Deployment Steps</h2>

1. Create the domain controller and client VMs in Azure
2. Install AD DS and promote the server to a domain controller
3. Create organizational units and an admin account
4. Join Client-1 to the domain
5. Allow domain users to use Remote Desktop on Client-1
6. Bulk-create users with PowerShell

<h3>1. Create the Virtual Machines</h3>

<img src="https://i.imgur.com/EWaMWLA.png" alt="Domain controller and client VMs in Azure"/>

I created two VMs in Azure, a Windows Server 2022 domain controller (DC-1) and a Windows 10 client (Client-1), in the same resource group and virtual network so they can communicate privately.

<!-- If you set DC-1's private IP to static, add: -->
<!-- I set DC-1's private IP address to static so it never changes. Client-1 relies on this address for DNS, and a changing IP would break domain lookups. -->

<h3>2. Install AD DS and Promote the Domain Controller</h3>

<img src="https://i.imgur.com/cHa8m9A.png" alt="Installing Active Directory Domain Services"/>
<img src="https://i.imgur.com/9x7lWwz.png" alt="Promoting the server to a domain controller"/>

On DC-1, I installed **Active Directory Domain Services** and promoted the server to a domain controller, creating a new forest with the domain **mydomain.com**. After the required restart, I logged back in with the domain account `mydomain.com\labuser`.

<img src="https://i.imgur.com/7VGqpOr.png" alt="Logging in with the domain account"/>

<h3>3. Create Organizational Units and an Admin Account</h3>

<img src="https://i.imgur.com/ogwZvgs.png" alt="Organizational units in Active Directory Users and Computers"/>

In Active Directory Users and Computers, I created two organizational units (OUs), **_EMPLOYEES** and **_ADMINS**. I created a new account in _ADMINS, added it to the **Domain Admins** group, and logged in with it to confirm the admin rights worked.

<img src="https://i.imgur.com/bNiWLDZ.png" alt="Admin account added to Domain Admins"/>
<img src="https://i.imgur.com/lCYm4vW.png" alt="Logged in as the new admin account"/>

Using a dedicated admin account instead of the built-in one follows best practice: privileged activity is tied to a named person, and day-to-day work can be done from a separate, non-admin account.

<h3>4. Join Client-1 to the Domain</h3>

<img src="https://i.imgur.com/brX7hKj.png" alt="Client-1 joined to mydomain.com"/>
<img src="https://i.imgur.com/tfLfKbK.png" alt="Client-1 visible in Active Directory"/>

Before joining the domain, I set Client-1's DNS server to DC-1's private IP address. Domain members find the domain controller through DNS, so the join fails without this. I then joined Client-1 to **mydomain.com**, restarted it, and confirmed on DC-1 that Client-1 appeared in Active Directory.

<h3>5. Allow Domain Users to Use Remote Desktop</h3>

<img src="https://i.imgur.com/ozs0zuD.png" alt="Remote Desktop settings on Client-1"/>

On Client-1, I configured Remote Desktop to allow domain users to log in remotely. In production, this access is normally limited to specific groups and enforced with Group Policy rather than configured on each machine.

<h3>6. Bulk-Create Users with PowerShell</h3>

<img src="https://i.imgur.com/cUN0uhI.png" alt="PowerShell ISE running the user creation script"/>
<img src="https://i.imgur.com/jPpXbVn.png" alt="Script output creating users"/>

On DC-1, I ran a PowerShell script in PowerShell ISE (as administrator) that created a large number of user accounts in the _EMPLOYEES OU.

<img src="https://i.imgur.com/4HFh3Hd.png" alt="Created users in the _EMPLOYEES OU"/>
<img src="https://i.imgur.com/QaVNLRN.png" alt="Logging in to Client-1 as a created user"/>

I then logged in to Client-1 as one of the new users to confirm the accounts worked. In a real environment, bulk-created accounts should be required to change their password at first logon instead of keeping a shared default.
