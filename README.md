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
Install RAS/ NAT:  <br/>

- <b>The reason why we have to install RAS / NAT is because it will allow us (after creating the windows 10 client) to have the created client on the private virtual network and still access the internet through the domain controller (DC)</b>
- <b>Select add roles and features</b>

<p align="center">
<img src="https://i.imgur.com/UvVfdub.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Select Remote Access role to install</b>

<p align="center">
<img src="https://i.imgur.com/V24mzVb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Select to install Routing and the DirectAccess and VPN will be automatically selected as well</b>

<p align="center">
<img src="https://i.imgur.com/b21GUHB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure RAS/ NAT:  <br/>

- <b>After the installation has finished, select Tools and then go to Routing and Remote Access </b>
- <b>Select the DomainControlle and go to Configure and Enable Routing and Remote Access </b>

<p align="center">
<img src="https://i.imgur.com/h4UbK3A.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Install NAT</b>

<p align="center">
<img src="https://i.imgur.com/Y7QkNrL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Here we will select the external network interface and then press next</b>

<p align="center">
<img src="https://i.imgur.com/ecWogQv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/PLaOFA7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install DHCP:  <br/>

- <b>This will allow the windows 10 clients to get an IP address that will give them access to the internet even though they are on the private internal network</b>
- <b>Same principle applies for schools</b>
- <b>Same as previously, select add roles and features however this time we will be selecting the DHCP Server features to be installed</b>

<p align="center">
<img src="https://i.imgur.com/tIb23Ld.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure DHCP:  <br/>

- <b>After the installation has finished, select Tools and then go to DHCP </b>
- <b>Now we can set up a scope that will generate the IP addresses in the selected range (172.16.0.100 - 200)</b>

<p align="center">
<img src="https://i.imgur.com/ICU1pQA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/2S1jrHg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The bellow section refferes to the duration that a pc will have the same exact IP address when accessing the specific network and no one else can have that specific IP address until the time expires</b>

<p align="center">
<img src="https://i.imgur.com/fqg5jkR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The clients will be using this specific nick of the domain controller as their default gateway / router</b>

<p align="center">
<img src="https://i.imgur.com/kaCuZdX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>After the configuration has been finalised, select the domaincontroller.domain.com and authorise it and then refresh it </b>

<p align="center">
<img src="https://i.imgur.com/zHvU1Ex.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create users using PowerShell:  <br/>

- <b>Make a configuration that lets us browse the internet from the domain controller </b>
- <b>However, this is not recommended do to in a production environment </b>
- <b>The reason why we are doing this now is because we want to search for and download the PowerShell script that is used to create the users</b>
- <b>Select configure this local server and from there select IE enhanced security confirmation and turn them off to have a smooth navigation on the web without being constantly spammed by security pop-ups</b>

<p align="center">
<img src="https://i.imgur.com/7F6sz9t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The PowerShell scrip contains 100 of random generated names</b>

<p align="center">
<img src="https://i.imgur.com/kvKZ2s9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Afterwards navigate to Windows PowerShell ISE and make sure you run it as administrator</b>
- <b>On the next step, open the powerShell script that we previously donwloaded</b>

<p align="center">
<img src="https://i.imgur.com/0wh7dtE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Script setup:  <br/>

- <b>Before running the scrip we have to enable the execution of all scripts on the server</b>
- <b>Beecause this is a security feature, we have to be careful with it</b>

<p align="center">
<img src="https://i.imgur.com/RlLeY51.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Create the users by running the script</b>

<p align="center">
<img src="https://i.imgur.com/Lm9YkKK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ZmAb1DG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/88jteR5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup Windows 10:  <br/>

- <b>Check if the IP address matches, same as the default gateway with what we previously assigned</b>

<p align="center">
<img src="https://i.imgur.com/OmSLdl4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/HwVeLIZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Join Windows 10 to the domain:  <br/>

- <b>Change the name of the PC to client1 and join the domain created by accessing Rename this PC (advanced) from the system's settings</b>
- <b>Join the domain by inserting the domain admin account username and password, otherwise it is not going to work if you use a regular user account</b>
- <b>Afterwards, you will be required to restart the PC</b>

<p align="center">
<img src="https://i.imgur.com/Jbakl5P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>We can see that the Windows 10 client has automatically reached out to the DHCP server and requested an IP address and now we've got the lease</b>

<p align="center">
<img src="https://i.imgur.com/KUrlyyO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/LcKTANB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Since the client is joined to the domain, then we will be able to login with any of the user accounts created previously to that machine</b>

<p align="center">
<img src="https://i.imgur.com/1SkTGPQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/bdwArET.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
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
