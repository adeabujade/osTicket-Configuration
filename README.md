<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Steps</h2>

**1. Create an Azure Virtual Machine**

**2. In the Virtual Machine download and install osTicket**


<h2>1.Azure Virtual Machine</h2>

**1. Create a Resource Group**

    a. Give the resource group a name (I chose os-Ticket)
   
    b. For Region choose (US) East US 2

    c. Press Review + Create and then create again

**2. Deploy a Windows 10 Virtual Machine (VM):**

    a. Assign it to the newly created Resource Group.

    b. During the VM setup, allow the creation of a new Virtual Network (VNet) and Subnet.

    c. For the image select Windows 10 Pro

    d. For the size select any with 2 vcpus

    e. Create a username and password for the VM

    f. Press Review + Create and then create again

The Resource Group should look like this after you configure the Virtual Machine.

![image](https://github.com/user-attachments/assets/fde0ae33-f397-4d3c-a4c5-7fc6c72bdba9)

**3. Accessing the Virtual Machines through Remote** 

    a. Open Remote Desktop through Windows search bar

    b. Go into the Virtual Machine that was just ticket and enter the public ip address

    c. Enter the Username and password for the VM

   ![image](https://github.com/user-attachments/assets/f90430f9-6e33-49cf-a695-b184b745f498)

   ![image](https://github.com/user-attachments/assets/3d082352-ae9b-4912-b89f-e62bac0e66e2)


<h2>2.osTicket Installation</h2>

**Step 1: Download and Prepare osTicket Installation Files**

**1.Download osTicket Installation Files:**

    a.Within the osticket-vm, download the [osTicket-Installation-Files.zip](url). The folder will be named osTicket-Installation-Files.
    
    b.Drag the file onto the desktop right click and press extract all

![image](https://github.com/user-attachments/assets/cd9ac450-c64a-49de-9aff-06adb6657d87)


**Step 2: Install IIS with CGI**

**1.Enable IIS and CGI:**

    a.Open Control Panel > Turn Windows features on or off

    b.Enable Internet Information services

    C. Enable CGI
    
        -Internet Information Services > World wide Web Services > Application Development Features 

    If it's done correctly, you can go to Microsoft Edge and go to the url 127.0.0.1 The page should look like this.

![image](https://github.com/user-attachments/assets/cd166289-4d93-45c6-9e4e-675f3379f975)

    


**Step 3: Install PHP Manager for IIS**

**1.Install PHP Manager for IIS:**

    a.From the osTicket-Installation-Files folder, run the installer PHPManagerForIIS_V1.5.0.msi.

![image](https://github.com/user-attachments/assets/bd3bd579-95c2-40f4-bd49-3b0d76526c4b)


**Step 4: Install Rewrite Module**

**1.Install the URL Rewrite Module:**

    a.From the osTicket-Installation-Files folder, install the rewrite_amd64_en-US.msi module.
    
![image](https://github.com/user-attachments/assets/628318ff-3e96-4297-bef2-3b5469693c18)


**Step 5: Set Up PHP**

**1.Create PHP folder:**

    a.Create a new folder on the C: drive: C:\PHP.
    
        -This PC > Window (C:)


**2.Install PHP:**

    a.From the osTicket-Installation-Files folder, extract php-7.3.8-nts-Win32-VC15-x86.zip into the C:\PHP folder.**

**3.Install Visual C++ Redistributable:**

    a.From the osTicket-Installation-Files folder, run VC_redist.x86.exe to install the required libraries for PHP.

Installations of PHP and Visual C++ Redistributable files.

![image](https://github.com/user-attachments/assets/f2051523-9d77-4989-9ee6-a5639bb35251)


**Step 6: Install MySQL:**

1. Install MySQL

    a.From the osTicket-Installation-Files folder, run the MySQL installer mysql-5.5.62-win32.msi.
   
    b.Choose Typical Setup and then click Launch Configuration Wizard after installation.
   
    c.In the wizard, select Standard Configuration and set the credentials:
        -Username: root
        -Password: root
![image](https://github.com/user-attachments/assets/822281d9-6ea7-4690-a584-4daf2173ef5a)


**Step 7: Register PHP in IIS**

**1.Open IIS Manager as Administrator.**

![image](https://github.com/user-attachments/assets/b5c25edf-eb4c-4a8f-b254-98ca42256ba1)


**2.Register PHP:**

    a.In PHP Manager for IIS, register PHP by browsing to C:\PHP\php-cgi.exe.
    
**3.Reload IIS:**

    a.Open IIS Manager, stop the server, and then restart it.

**Step 8: Install osTicket**

**1.Extract osTicket Files:**

    a.From the osTicket-Installation-Files folder, extract osTicket-v1.15.8.zip.

    b.Copy the upload folder into C:\inetpub\wwwroot.

**2.Rename the Folder:**

    a.Inside C:\inetpub\wwwroot, rename the upload folder to osTicket.

![image](https://github.com/user-attachments/assets/e1fcd35d-0efe-4c19-8b83-183baf6f9cdb)


**3.Reload IIS:**

    a.Open IIS Manager, stop the server, and then start it again.

**4.Browse osTicket Site:**

    a.In IIS Manager, go to Sites > Default > osTicket and click *Browse :80 to test access.

![image](https://github.com/user-attachments/assets/5d9f1535-a7f9-457b-8e17-1294108065ff)




**Step 9: Enable PHP Extensions**

**1.Enable PHP Extensions:**

    a.Go back to IIS Manager, then to Sites > Default > osTicket.

    b.Double-click PHP Manager.

    c.Click Enable or disable an extension and enable the following extensions:

        -php_imap.dll
    
        -php_intl.dll
    
        -php_opcache.dll
    
**2. Refresh osTicket:**

    a.Refresh the osTicket site in your browser and check the changes.

![image](https://github.com/user-attachments/assets/67381153-6263-4dbe-806c-2d43b4a21b9d)


**Step 10: Configure osTicket**

**1. Rename ost-config.php:**

    -From C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, rename it to ost-config.php.

**2 .Set Permissions for ost-config.php**

    -Right-click ost-config.php, select Properties > Security.
    
    -Click Disable inheritance and then Remove All.
    
    -Add Everyone with Full Control.

**Step 11. Finalize osTicket Setup**

**1.Continue osTicket Setup in the Browser:**

    a. Open the osTicket setup page and enter the following details:
    
        -Helpdesk Name: Name your helpdesk.
        
        -Default Email: Set an email address to receive tickets.
        
**2. Install HeidiSQL:**
    a.From the osTicket-Installation-Files folder, install HeidiSQL.

   
**3. Create MySQL Database:**

    a.Open HeidiSQL and create a new session with the following:
   
        -Username: root
   
        -Password: root
   
    b.Connect to the session and create a database named osTicket.

![image](https://github.com/user-attachments/assets/7a08deda-f03b-4564-8751-898c2a07dc60)

   
**4. Complete osTicket Setup:**

    a.In the browser setup:

        -MySQL Database: osTicket

        -MySQL Username: root

        -MySQL Password: root

![image](https://github.com/user-attachments/assets/2bb3f5db-f18b-407a-a95e-2acd3269e87c)


**Step 12. Verify Installation**

    1. Browse to Login Page: After a successful installation, go to your helpdesk login page: http://localhost/osTicket/scp/login.php
    
    2.End User osTicket URL: The end-user portal can be accessed at: http://localhost/osTicket/

<h2>Helpdesk Login</h2>

![image](https://github.com/user-attachments/assets/06af0569-65fb-41c3-bad5-e2d6c2949e63)

<h2>End user Portal</h2>

![image](https://github.com/user-attachments/assets/b2b87c4e-8f6a-44e1-87c8-cb4a01a8df17)




