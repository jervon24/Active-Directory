<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Windows Server and Windows 10 Virtual Machine in Azure
- Install Active Directory
- Create Organizational Units in Active Directory
- Configure and work with both virtual machines

<h2>Deployment and Configuration Steps</h2>

<p>
<img src=https://i.imgur.com/EWaMWLA.png/>
</p>
<p>
The image above shows both virtual machines being created in Azure.They were both in the same virtual network and resource group.
</p>
<br />

<p>
<img src=https://i.imgur.com/cHa8m9A.png/> <img src=https://i.imgur.com/9x7lWwz.png/>
</p>
<p>Active Directory Domain Services was installed then the server was promoted to a domain controller as shown in the second picture with a domain name of "mydomain.com" Windows server virtual machine restarted to completed the installation of domain services. Since a new domain was created, I then had to log back in as "mydomain.com\labuser as shown in the picture below.

<img src=https://i.imgur.com/7VGqpOr.png/>



s nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
