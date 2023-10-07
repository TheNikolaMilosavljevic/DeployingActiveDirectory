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

- Create windows server virtual machine using Microsoft Azure
- Ensure connectivity between client and domain controller
- Install active directory
- Create an admin as well as a normal user in active directory
- Join client-1 to your domain
- Setup remote desktop for non-administrative users on client-1
- Create additional users and attempt to log into client-1 with the accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<a href="https://imgbox.com/J9sH7XUY" target="_blank"><img src="https://thumbs2.imgbox.com/96/c1/J9sH7XUY_t.png" alt="image host"/></a>
</p>
<p>
Using your Microsoft Azure account, create a virtual machine named DC-1, this particular virtual machine will be running Mircosoft Server 2022. Make sure to use at least 2 processors for this machine in order for the virtual machine to run with adequate speed.
</p>
<br />

<p>
<a href="https://imgbox.com/AOvKPOhA" target="_blank"><img src="https://thumbs2.imgbox.com/9d/be/AOvKPOhA_t.png" alt="image host"/></a>
  Edit the DC-1 server you created by changing the ip configurations from dynamic to static under virtual machines > DC-1|Networing > dc-1164|Ip configurations
</p>
<br />

<p>
<a href="https://imgbox.com/FqvUSleT" target="_blank"><img src="https://thumbs2.imgbox.com/a5/28/FqvUSleT_t.png" alt="image host"/></a></p>
<p>
Using client-1 in virtual machine open the command prompt and ping the private Ip address of you other virtual machine called DC-1. Make sure that you turn off the fire wall in DC-1 in order to have a successful ping
</p>
<a href="https://imgbox.com/ID5dTPo3" target="_blank"><img src="https://thumbs2.imgbox.com/20/c8/ID5dTPo3_t.png" alt="image host"/></a>
Install active directory DC-1 by clicking on "server manager", then click "add roles and features", go through the prompts and make sure you check "active directory domain services" then install.
<p></p>
<br />
<a href="https://imgbox.com/fQklGRyC" target="_blank"><img src="https://thumbs2.imgbox.com/e1/8b/fQklGRyC_t.png" alt="image host"/></a>
Create a new organizational unit called "_Employees" as well as a new organizational unit called "_Admins". Using the organizational units, this grants the ability to add or remove users at your discretion.
<a href="https://imgbox.com/KcszsYa2" target="_blank"><img src="https://thumbs2.imgbox.com/44/ac/KcszsYa2_t.png" alt="image host"/></a>
Click the admins tab and in the file right-click and click add user. Create a new user and password named "Jane_Admin". To make this user an actual domain admin, right click and add the "Jane_Admin" to the domain admins group. It is good practice to use a specific user as opposed to a generic "Admin" user.
<a href="https://imgbox.com/nQ9r3fJy" target="_blank"><img src="https://thumbs2.imgbox.com/52/29/nQ9r3fJy_t.png" alt="image host"/></a>
In order to join client-1 to your domain, client-1 must adopt the same DNS number as the DC-1 server. Using Microsoft Azure, edit client-1 one's DNS number. Restart Client-1
<a href="https://imgbox.com/rnA3Rt2a" target="_blank"><img src="https://thumbs2.imgbox.com/be/8d/rnA3Rt2a_t.png" alt="image host"/></a>
Now that you have joined Client-1 is on the domain, you can log in as "Jane_admin" in Client-1
