<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- 1: Set up Resources in Azure
- 2: Ensure Connectivity between the Client and Domain Controller
- 3: Install Active Directory
- 4: Create an Admin and Normal User Account in Active Directory
- 5: Join Client-1 to your Domain
- 6: Setup Remote Desktop for non-administrative users on Client-1
- 7: Create users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<h2>1. Setup Resources in Azure</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside Azure, create 2 Virtual Machines(VMs). First one will be Domain Controller or "DC-1" using Windows Sever 2022,
the second is "Client-1" using Windows 10. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Be sure to check that both VMs are on the same V-net. In Azure,
set "DC-1's" ping assignment to Static(Very important!)
</p>
<br />


<h2>2. Ensure Connectivity between te Client and Domain Controller</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
