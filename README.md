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
- Configure and work within both virtual machines

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
<p>Active Directory Domain Services was installed then the server was promoted to a domain controller as shown in the second picture with a domain name of "mydomain.com" Windows server virtual machine restarted to complete the installation of domain services. Since a new domain was created, I then had to log back in as "mydomain.com\labuser as shown in the picture below.

<img src=https://i.imgur.com/7VGqpOr.png/>



<img scr=https://i.imgur.com/ogwZvgs.png/>
</p>
<p> 
  
  Two organizational units were created in active directory; _EMPLOYEES and _ADMIN. I added a member to the admin unit and gave that member administrial authority. I then relogged in as the member to have a real life experience as shown in the snapshots below.
  
 <img src=https://i.imgur.com/bNiWLDZ.png/> <img src=https://i.imgur.com/lCYm4vW.png/>

<p>
  
  Client-1 Virtual machine (windows10) was then joined to the Domain Controller virtual machine as shown in the picture below. Before this happen, client-1 DNS settings was set to the domain controller private IP address so that client-1 could join successfully. I then connected to active directory in the domain controller virtual machine then checked wheather client-1 virtual machine was connected. Client-1 was then added to the computers file as shown in the second picture. 

  <img src=https://i.imgur.com/brX7hKj.png/> <img src=https://i.imgur.com/tfLfKbK.png/>
>
</p>
<p>
I then changed the settings in CLient-1 vitual machine so that other users could remote desktop into the computer. The screenshot below displays this.
  
<img src=https://i.imgur.com/ozs0zuD.png/>
</p>


I then accessed the domain controller and opened Powershell ISE as an administrator to run a code which will create many users in the _EMPLOYEES organizational unit. Afterwards I then logged in as one of the users which were created. The images below shows this and thus brings an end to this section of the lab.

<img src=https://i.imgur.com/cUN0uhI.png/> <img src=https://i.imgur.com/jPpXbVn.png/> <img src=https://i.imgur.com/4HFh3Hd.png/> <img src=https://i.imgur.com/QaVNLRN.png/>


