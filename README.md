# Configuring Group Policy
<h2>Description</h2>
This is a walkthrough on creating a Group Policy Object (GPO) to creates a File Share and install Notepad++ to connected Windows 10 clients. In the future, If I scale up the number of clients, having a GPO handle install this software is much faster than manually installing it on every machine.
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
Now that the installer is accessable, I create the GPO. 
