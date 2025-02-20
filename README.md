<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<!--<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)
- 
-->
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine & Connect via Remote Desktop
- Install IIS, PHP, and Required Modules
- Install MySQL & Configure IIS for PHP
- Install & Configure osTicket
- Set Up osTicket & Final Configurations


<h2>Installation Steps</h2>

<p>
<b>Step 1: Create an Azure Virtual Machine & Connect via Remote Desktop</b>
  

</p>
<img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/57ca42baa7de00b7e19d3006019cfb3a1039eac2/CreatenewVM.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>

<p>
Create an Azure Virtual Machine
<p>
<img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/76c5b945ac6481e0d467c39aa9e2195a4f5e2be7/customizeVM.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
OS: Windows 10
vCPUs: 4
Name: osticket-vm
Username: labuser
Password: osTicketPassword1!
</p>
<p>
  Log in to the VM using Remote Desktop (RDP).
  <p>
  <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/fae8f7b5fc522de4da0d064eb893dc2e1e09597b/logintoremotedesktop.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
  </p>
</p>
<br />

<p>
## **Step 2: Install IIS, PHP, and Required Modules**
</p>
<p>
### **Enable IIS with CGI**
- Go to **Control Panel** → **Programs and Features** → **Turn Windows features on or off**.  
- Under **Internet Information Services (IIS)** → **World Wide Web Services** → **Application Development Features**, enable:  
  - ✅ CGI 
  <p>
  <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/27c3b8a87894e947c1645258fb900af304803cfc/EnableIIS_w_cgi.png" height="30%" width="30%"/>
  </p>
</p>
<p>
### **Install Required Components**
- Install the following from the `osTicket-Installation-Files` folder:  
  - **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`)  
  - **Rewrite Module** (`rewrite_amd64_en-US.msi`)  
  - **VC_redist.x86.exe**  
  <p>
    <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/5444e2331c1dbe962e17d127b344ff7ae901ec54/install_PHPmanager_install_rewriteModule.png" height="30%" width="30%"/>
  </p>
</p>
<p>
### **Set Up PHP**
- Create a new directory:
  ```sh
  C:\PHP
  <p>
    <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/325a2578546ed1bbc493e6819eec954ea35a9268/PHP_directory.png" height="30%" width="30%"/>
  </p>
</p>
<p>
  Extract php-7.3.8-nts-Win32-VC15-x86.zip into C:\PHP.
  <p>
    <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/325a2578546ed1bbc493e6819eec954ea35a9268/Extract_PHP_7.3.8.png" height="30%" width="30%"/>
  </p>
</p>
<br />

<p>
<b>Step 3: Install MySQL & Configure IIS for PHP</b>
</p>
<p>
Install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
<p>
<img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/0815ca5b7ece0de72614866cf66b845a4a956685/install_mysql.png" height="30%" width="30%"/>
</p>
Setup Type: Typical
Launch Configuration Wizard → Standard Configuration
Username: root
Password: root
<p>
  <img src="https://github.com/Drew-Stokes/osTicket_Prerequsites_Instalation/blob/0815ca5b7ece0de72614866cf66b845a4a956685/install_mysql.png" height="30%" width="30%"/>
</p>
</p>
<p>
  Configure PHP in IIS

Open IIS Manager.
Go to PHP Manager → Register new PHP version → C:\PHP\php-cgi.exe.
Reload IIS (Stop & Start Server).
</p>
<br />
<p>
<b>Step 4: Install & Configure osTicket</b>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install osTicket v1.15.8

Extract osTicket-v1.15.8.zip.
Copy the upload folder to C:\inetpub\wwwroot.
Rename upload to osTicket.
</p>
<p>
  Reload IIS & Open osTicket in Browser

In IIS, go to Sites → Default Web Site → osTicket.
Click *Browse :80.
</p>
<p>
  Configure ost-config.php

Rename:
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
Assign Permissions:
Disable inheritance → Remove All
Add new permissions → Everyone → Full Control
</p>
<br />
<p>
<b>Step 5: Set Up osTicket & Final Configurations</b>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Complete osTicket Setup in Browser
Name your Helpdesk.
Set a default email for customer support.
</p>
<p>
  Set Up MySQL Database in HeidiSQL
Install HeidiSQL.
Open HeidiSQL → Create a new session (root/root).
Connect & Create a database called osTicket.
</p>
<p>
  Finalize osTicket Setup
In the browser, enter:
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root

Click Install Now!
</p>
<p>
  Secure Installation

  Delete the setup folder:
  C:\inetpub\wwwroot\osTicket\setup

Set C:\inetpub\wwwroot\osTicket\include\ost-config.php to Read-only.

http://localhost/osTicket/scp/login.php

http://localhost/osTicket/

</p>
