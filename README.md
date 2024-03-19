# Configuring Group Policy
<h2>Description</h2>
This is a walkthrough on creating a Group Policy Object (GPO) to install Notepad++ to connected Windows 10 clients. This GPO grabs the Notepad++ instal from a File Share named Share on the network. In the future, If I scale up the number of clients, having a GPO handle install this software is much faster than manually installing it on every machine.
<h2>Environments Used </h2>
- <b>Windows Server 2019</b> (17763) </br>
- <b>Windows 10</b> (22H2)
<h2>Utilities Used</h2>
- <b>PowerShell</b>
<h2>Group Policy Configuration Walkthrough</h2> 
To start, I create a folder named Share containing a Notepad++ installer on the Domain Controller. I configure Share Permissions to allow Authenticated Users to read from the folder, and to allow Domain Admins to have Full Control. When I check into my Windows 10 client, the Share folder appears when accessing \\DC\.
<img src="https://i.imgur.com/dpfEvRd.png" alt="Share"/>
<img src="https://i.imgur.com/J1EY5LN.png" alt="Share"/>
<br/>
Now that the installer is accessable, I create a GPO link for my _DOMAIN_COMPUTERS Organizational Unit (OU) called Notepad++ Install. Under Group Policy Management Editor, I created a package that points to the N++ installer in the network share. I then run /gpupdate on the DC and client to initiate the Group Policy update.
<img src="https://i.imgur.com/rlsYGrN.png" alt="GPO Link"/>
<img src="https://i.imgur.com/yVq0tlW.png" alt="GPME Package"/>
<img src="https://i.imgur.com/g7RTKef.png" alt="/gpupdate force"/>
<br/>
After restarting, I'm able to log in and open Notepad++ on my machines.
<img src="https://i.imgur.com/CBM2u7O.png" alt="Notepad++"/>
<br/>
