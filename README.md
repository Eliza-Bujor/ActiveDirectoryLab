<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
The project consists of a walk through on how to create an Active Directory Lab Environment on Virtual Box. This project has helped me develop my understanding on how active directory works, as well as windows networking.
<br />

<h2>Environments Used </h2>

- <b>Windows Server 2019</b>
- <b>Windows 10</b>

<h2>Program walk-through:</h2>

<p align="center">
Installing Server 2019: <br/>

- <b>Before starting the VM and installing the Server 2019, we assigned 2 network adapters</b> <br />

<p align="center">
<img src="https://i.imgur.com/vIJGrFh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ay4i2cO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/cp5H9Dv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setting up the server network adapters:  <br/>

- <b>Because the NIC that is on the internet will automatically get an IP address from the home router, it doesn't require to be set it up</b>
- <b>However, on the other hand, the NIC that is on the internal side, it has to be set </b>

<p align="center">
<img src="https://i.imgur.com/JwRbCjd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/GUHlRNx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>On the internal NIC one we will be assigning an IP as the adapter was automatically searching for a DHCP server to get an IP address, hence the IP 169.254.87.223</b>

<p align="center">
<img src="https://i.imgur.com/8S5I18g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- <b>There is no need to set a default gateway as the domain controller itself will be acting as the default gateway</b>
- <b>For the DNS we set it to the generic loopback address which will make reference to ourselves</b>

<p align="center">
<img src="https://i.imgur.com/r2jqhFG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Rename the Server: <br/>


<img src="https://i.imgur.com/9Sp7mNK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install active directory domain services:  <br/>
<img src="https://i.imgur.com/hvwrLp3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/LApdoKL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create the domain:  <br/>

- <b>After the installation of the active directory domain, we need to perform a post-deployment configuration to create the domain</b>

<p align="center">
<img src="https://i.imgur.com/ZOGs6D0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/jE1RHnE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create domain admin account:  <br/>
<img src="https://i.imgur.com/0NJ2hzE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- <b>After the user has been created, add a new Domain Admins profile</b>
- <b>On the domain.com add a new object of the type organizational unit</b>

<p align="center">
<img src="https://i.imgur.com/FxtryN7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- <b>The last step will be to logout and log back in</b>

<p align="center">
<img src="https://i.imgur.com/Y9JUqyA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Observe the wiped disk:  <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
