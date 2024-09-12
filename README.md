<h1>Active Directory Lab</h1>

<h2>Description</h2>
In this project, I set up a Windows Server and configured a root domain for Active Directory.  While setting up this Windows server I also set up a DHCP server and Remote Access to allow for an internal network to be created. I customized the network's IP address range for automatic assignment via the DHCP server. I also created multiple users and connected a second virtual machine as a client that allowed users to log in across the network and verified that everything was working properly. <br />


<h2>Utilities Used</h2>

- <b>Active Directory</b> 
- <b>DHCP</b>
- <b>Windows / Windows Command Prompt</b>
- <b>VMware</b> 

<h2>Project walk-through:</h2>

<p align="center">
The setup in VMWare, installing Windows Server 2022 and a Windows VM (Using Windows 11): <br/>
<img src="https://i.imgur.com/RyoUIVc.png"/> 
<br />
<br />
I started the project off in the Windows Server 2022 and added the Active Directory Domain Service feature: <br/>
<img src="https://i.imgur.com/ufoo5Gp.png"/> 
<br />
<br />
During the setup, I added a new forest and named my root domain name nick.grady: <br/>
<img src="https://i.imgur.com/R73SarK.png"/> 
<br />
<br />
After Active Directory Domain Service was successfully installed, I opened the Active Directory User and Computer and added in a new Organizational Unit for Admin accounts and added in a new user Nicholas Grady, using the organizations naming convention of "a-ngrady" for the account.  For the rest of the Lab I log out of the default domain admin account and log into a-ngrady as a best practice for security/auditing: <br/>
<img src="https://i.imgur.com/pWKk9S9.png"/> 
<br />
<br />
I edited the user Nicholas Grady to add to the Domain Admins group:
 <img src="https://i.imgur.com/mtB8rd8.png"/> 
<br />
<br />
Added the feature for allowing Remote Access into the Windows Server 2022
 <img src="https://i.imgur.com/wkxmM4I.png"/> 
<br />
<br />
Opened the Routing and Remote Access tool and configured and enabled routing and remote access:
 <img src="https://i.imgur.com/zJiASeB.png"/> 
<br />
<br />
I set up the Remote Access Server to use NAT so that the internal network can use the internet through the Domain Controller to access the internet.  All computers in the network will be set up with an internal network and reach through the Domain Controller for internet access: 
 <img src="https://i.imgur.com/Ew8UxXC.png"/> 
<br />
<br />
Adding in another feature of DHCP to allow for the DHCP server to give out internal IP addresses: 
 <img src="https://i.imgur.com/uH8eWz3.png"/> 
<br />
<br />
After Installing the DHCP server, I opened the DHCP tool and added a new scope of IP addresses to be used for the internal network opening up IP ranges 172.16.0.100 to 172.16.0.200:
 <img src="https://i.imgur.com/INdydZv.png"/> 
<br />
<br />
As a last step, I opened up Active Directory again to add another Organizational Unit and added a User group.  I populated this with new user accounts using randomized names and added a non-admin account under my name "ngrady" using the organization's user account naming policy of first name's first letter followed by the full last name for all accounts:
 <img src="https://i.imgur.com/fvkdKKC.png"/> 
<br />
<br />
Now that the server was all set up, I installed the Windows 11 virtual machine and used the command prompt to ensure connectivity, successfully connected to the default gateway (which is the IP of the Domain Controller) as well as being automatically assigned the IP 172.16.0.100 through the DHCP server: 
 <img src="https://i.imgur.com/Nn513gb.png"/> 
<br />
<br />
Further testing, ensuring their is internet access using the Ping command successfully reaching google and ensuring the Windows 11 VM can reach the Domain by pinging it with "ping nick.grady":
 <img src="https://i.imgur.com/FPCYEfE.png"/> 
<br />
<br />
Opened System settings to change use the advanced name change feature to change the computer name to "Client1" and join the Domain of nick.grady: 
 <img src="https://i.imgur.com/fan3Fze.png"/> 
<br />
<br />
Moved back to the Microsoft Server 2022 VM to ensure the new "Client1" is showing up in the DHCP server: 
 <img src="https://i.imgur.com/8WpoFwM.png"/> 
<br />
<br />
Confirming the Windows 11 computer shows up in Active Directory: 
 <img src="https://i.imgur.com/QixgzYE.png"/> 
<br />
<br />
Switching back to the Windows 11 VM with user ngrady logging in:
 <img src="https://i.imgur.com/a8zublO.png"/> 
<br />
<br />
Success! Users are now able to use their credentials to log into Client1:
 <img src="https://i.imgur.com/7XElkXY.png"/> 
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
