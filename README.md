<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This explanation outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Windows Virtual Machine)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Environment and accounts needed for Active Directory creation and testing
- Set up Active Directory and configure Organizational Units
- Connect Client to Domain Controller via IP and DNS configuration
- Test that User accounts could connect to the Domain and Client via Remote Desktop

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/YUrSqdQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first step was to create the main environment for Active Directory which was the Domain Controller Virtual Machine as well as the virtual network for the operating system to run on. Another resource was the simulated Client that will be later added to the Domain, this Client was added under the same virtual network as the Domain Controller. An Admin account was created as well to access all of these resources.
</p>
<br />

<p>
<img src="https://i.imgur.com/rWqw13H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After connecting to the Domain Controller via Remote Desktop I enabled Active Directory and set up a new "forest" in the Server Manager which was provided by default in the Domain Controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/wmif7fN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that Active Directory was up and running I created two new Organizational Groups for the Domain Admins and Domain Users and configured permissions accordingly to both, as well as individual permissions per group and account as accounts were added.
</p>
<br />

<p>
<img src="https://i.imgur.com/DHfswzd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to set the Domain Controllers IP address to be static via the virtual NIC provided to allow Clients to consistently connect to the Domain. In order to allow the Client to connect to the Domain, the default DNS server of the Client needed to be set as the Domain Controllers IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/u0kgPkE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that the Client was able to resolve the Domains IP address from the Domain name it was able to connect.
</p>
<br />

<p>
<img src="https://i.imgur.com/249u2uV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to allow Domain Users to log into the Client via Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/fYzWvRy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To test that any Domain User could access the Client and thus the Domain, I first ran a script in PowerShell ISE to create randomly generated user accounts in the Domain under the Users Organizational Unit.
</p>
<br />

<p>
<img src="https://i.imgur.com/MArcslv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After taking one of the randomly generated User accounts and signing into the Client via remote desktop as said User, it was evident that this User account was connected to the Domain via the Client.
</p>
<br />
