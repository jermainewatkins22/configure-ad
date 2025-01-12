<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This Step-by-Step tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




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
<img src="https://i.imgur.com/PeI5vY4.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside Azure, create 2 Virtual Machines(VMs). First one will be Domain Controller or "DC-1" using Windows Sever 2022,
the second is "Client-1" using Windows 10. 
</p>
<br />

<p>
<img src="https://i.imgur.com/qCDCqJD.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Be sure to check that both VMs are on the same V-net. In Azure,
set "DC-1's" NIC Private IP to Static(Very important!) Changing the IP address to static asures that the IP address won't change.
</p>
<br />


<h2>2. Ensure Connectivity between te Client and Domain Controller</h2>

<p>
<img src="https://i.imgur.com/IN4k9We.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to Client-1 with Remote desktop and ping DC-1's private IP 
address with ping -t and DC-1's private IP. The request should timeout
due to firewall on DC-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/MUmFko4.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
You must disable the firewall. Login to the Domain Controller(using Remote Desktop)
and enable ICMPv4 in the local Windows Firewall. In Client-1, check back to see if 
the ping was successful.
</p>
<br />


<h2>3. Install Active Directory</h2>
<p>
<img src="https://i.imgur.com/grS2erV.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In DC-1, Install Active Directory Domain Services.  

Service Manager/add roles/features->Active Directory Domain Services/install/open
</p>
<br />

<p>
<img src="https://i.imgur.com/Qoti1u1.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configure DC-1 and add a new forest with the root domain name of "mydomain.com"
</p>
<br />

<p>
<img src="https://i.imgur.com/AagPOXy.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Restart and then log back into DC-1 as user: "mydomain.com\user"
</p>
<br />


<h2>4. Create an Administrator Account and Normal User Account in Active Directory</h2>
<p>
<img src="https://i.imgur.com/HUEqn5G.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
In AD Users and Computers create two Organizational Units named "EMPLOYEES" AND "ADMINS"
</p>
<br />


<p>
<img src="https://i.imgur.com/Eh4ohIt.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new employee "Jane". Next add "Jane" to the Domain Admins group User-> Properties-> Member of-> "domains_admins" the text box-> apply close the RDP connection to DC-1 and reconnect into DC-1 as mydomain\Jane
</p>
<br />

<h2>5. Join Client-1 to your Domain</h2>

<p>
<img src="https://i.imgur.com/q0KxQNa.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>From the Azure Portal, set Client-1's DNS settings to the DC's Private IP address. Restart Client-1 in Azure.
</p>
<br />


<p>
<img src="https://i.imgur.com/0ke1kMN.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login into Client-1. as the original local Admin (labuser) and loin it to the Domain (Computer will restart)
</p>
<br />

<h2>6. Setup Remote Desktop for non-admin Users on Client-1</h2>

<p>
<img src="https://i.imgur.com/cy1PtcX.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Client-1 as mydomain.com\jane_admin and open system properties, click "Remote Desktop". Allow "domain users" access to the remote desktop. You acn now log into Client-1 as a normal, non-administrative user now.
</p>
<br />

<h2>7. Create users and attempt to log into client-1 with one of the users.</h2>

<p>
<img src="https://i.imgur.com/B4KQHNF.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into to DC-1 as jane_admin and open PowerShell_ISE as an Administrator. Then create a new file amd paste this script(https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)into the file. Run the script and observe the accounts being created. Open Users and Computers and observe the the accounts in the appropriate OU. Finally, attempt to log into Client-1 with one of the accounts. If able to log in, you have successfully set up Active Directory!
</p>
<br />



