# osTicket Installation and Prerequisites 

> [!Important]
> Things you'll need:
> - Microsoft Azure Account
> - A Virtual Machine running Windows 10
>   - For assistance in creating an account and Virtual Machine, please refer to the [Azure Crash Course Guide](https://github.com/EMoniSmall/azurecrashcourse).

<h2>Installing osTicket onto a Virtual Machine</h2>

> [!Note]
> osTicket runs through a website so the first step will be installing ISS which is essentially a web server.

Step 1: Once you're remotely logged into your Virtual Machine, from within the VM, open Internet Explorer and visit [this google drive for the osTicket Installation Files](https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) and download all of the files onto your VM.

Step 2: While the files are downloading open up the VM's control panel by right-clicking the start menu and selecting "Run". Enter "Control Panel" > select Programs > Turn Windows features on or off. 

![mstsc_XBe8o8Pks1](https://github.com/EMoniSmall/osInstall/assets/166156618/7c123e5f-cb1f-46d2-9e46-3e791804bcd2)


Step 3: Look for Internet Information Services and check the box next to it. Then expand the box. Expand World Wide Web Services > Expand Application Development Features > Check CGI. Collapse Application Development Features. 

![mstsc_3sO9T8Os1o](https://github.com/EMoniSmall/osInstall/assets/166156618/ad6c6667-7ba1-43c6-9182-a1caed9d7879)

Step 4: Expand Common HTTP Features and make sure everything is checked and hit OK.

![mstsc_vIwIgLO9gj](https://github.com/EMoniSmall/osInstall/assets/166156618/404d387b-3d80-48c8-8a84-9fa6f7d3e553)

> [!Note]
> To test if the connection worked, open a web browser and type in <b>127.0.0.1</b>. The following page should open:
> ![chrome_MLghEnRuIP](https://github.com/EMoniSmall/osInstall/assets/166156618/d14dd8da-fffd-40c5-b013-0d2de021578a)


<h2>Installation Files</h2>

Step 1: If you haven't already, visit [this google drive for the osTicket Installation Files](https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) and download the files. 

Step 2: From your downloaded files, install the PHP Manager for IIS (<b>PHPManagerForIIS_V1.5.0</b>).

Step 3: Next, install the Rewrite Module (<b>rewrite_amd64_en-US</b>)

Step 4: Once the Rewrite Module is installed, you'll need to create a directory on the local hard drive for PHP. (C:\PHP) Open up a file explorer> This PC > Windows (C:) > right-click create a new folder named "PHP."

Step 5: In your download folder, look for PHP 7.3.8 <b>(php-7.3.8-nts-Win32-VC15-x86.zip)</b> and extract it into your newly created C:\PHP folder. 

![mstsc_v2quU2ua5Z](https://github.com/EMoniSmall/osInstall/assets/166156618/95bdae23-4273-4418-9a66-fda2e04d1573)

Step 6: Next, install VC_redistx86.exe

Step 7: Install, MySQL 5.5.62 <b>(mysql-5.5.62-win32.msi)</b>. "Typical" installation. Make sure to check the box to Launch the MySQL Instance Configuration Wizard before clicking Finish. Choose Standard Configuration and enter a password that you'll remember. (Your Username will be root.)

> [!Note]
> This installs a database on the computer to store application data such as the tickets and users.

![mstsc_xKZFKXwgtV](https://github.com/EMoniSmall/osInstall/assets/166156618/1c1e39c6-d210-4d1c-84b9-99b5092b5231)

<h2>Configuring IIS as an Admin</h2>

Step 1: Click Start and type in IIS. You'll see Internet Information Services (IIS) Manager. Right-click and runas Administrator. 

> [!Note]
> You'll notice some options that you've installed already such as URL Rewrite and PHP Manager.
>  
> ![mstsc_ECtFk84TYR](https://github.com/EMoniSmall/osInstall/assets/166156618/d923f6eb-7b9b-404c-8e26-f8762f4c213b)
> ![mstsc_iVRaJoUGui](https://github.com/EMoniSmall/osInstall/assets/166156618/d2fc1bc7-4ba9-4600-986e-de1e9cbf5f81)

Step 2: Double-click PHP Manager > Register new PHP version > ... > PHP > Select php-cgi and Open.

![mstsc_4PfQkxkLLi](https://github.com/EMoniSmall/osInstall/assets/166156618/b3e7bb98-0ac9-4026-a0f8-153e05cbb706)

Step 3: Back on the Home screen of IIS Manager, on the right side of the window, under Manage Server, Click Restart. 

<h2>Installing osTicket</h2>

Step 1: Pull up your downloads folder and open up a 2nd File Explorer. On the 2nd File Explorer, go to This PC > Windows (C:) > inetpub > wwwroot.

Step 2: From your downloads folder, click into the osTicket-v1.15.8 and drag the Upload folder into wwwroot and allow the folder time to transfer. 

![mstsc_SePbCmz9Lu](https://github.com/EMoniSmall/osInstall/assets/166156618/1e7e2d9e-4d8d-4466-a381-c03af501b656)

Step 3: Rename "upload" to "osTicket"

Step 4: In IIS Manager, stop and start the server or Restart. 

![mstsc_YfZHNvJUlw](https://github.com/EMoniSmall/osInstall/assets/166156618/0b142398-ac5a-4152-b964-fc595ff4c8e0)

Step 5: Once the server has restarted, on the left of IIS Manager, open Sites > Default Websites > osTicket. On the Right, click on Browse *:80 (http) and the website for osTicket should appear. 

![mstsc_P01XhiSPgV](https://github.com/EMoniSmall/osInstall/assets/166156618/4cacf688-ae64-4a70-a240-be4dbc8abf54)

> [!Note]
> Some extensions aren't enabled as marked by the X's.

Step 6: Return to IIS Manager > Sites> Default Website > osTicket > Double-Click PHP Manager > Enable or Disable an Extension.

Step 7: Under the disabled list, look for php_imap.dll. Select it and click enable in the top right of the window.

Step 8: Look for php_intl.dll and enable.

Step 9: Look for php_opcache.dll and enable.

Step 10: Return to the osTicket Website and refresh the page. You should see some of the extensions become available. 

![mstsc_BVgeVbO13W](https://github.com/EMoniSmall/osInstall/assets/166156618/beef8b0a-855c-4c4b-84ce-66ca4d1b60b3)

Step 11: Open up a File Explorer > This PC > Windows (C:) > inetpub > wwwroot > osticket > include > search for ost-sampleconfig.php. Rename the file to ost-config.php.

Step 12: Right-click ost-config.php > Properties > Security > Advanced > Click Disable inheritance > Remove all permissions > Add > Select Principle > type in Everyone > Check name > Check Full Control > Ok.

> [!Note]
> The reason we need to disable inheritance and add new permissions is because I'm unsure which user actually interacts with this file. osTicket needs to be able to interact with the file so to make sure it works, we're giving access to everyone for now.

![mstsc_OBnVpPbYuA](https://github.com/EMoniSmall/osInstall/assets/166156618/0b29c8bf-b2d0-43ac-a1de-4d07de5115ea)

<h2>osTicket Settings</h2>

Step 1: Return to the osTicket Website and begin entering information for your helpdesk name, email ect... Remember the information entered here as this will be used as your log in info. 

Step 2: In your downloads folder, there is one more file to setup. HeidiSQL. Once it is done downloading and installing, allow it to launch. 

> [!Note] HeidiSQL will allow us to connect and setup the SQL database that osTicket is going to use.

Step 3: On the bottom left of the Heidi window, Click New on the bottom right. If you remember when setting up MySQL, you have a username "root" and a password you created along with it. Enter root under user if it hasn't already done so and enter the password you created. Return to the osTicket Website once done.

![mstsc_PddL9DSw9q](https://github.com/EMoniSmall/osInstall/assets/166156618/ef4c4823-a030-401c-b1ec-c6f6680958cf)

Step 4: Right-click Unamed > Create New > Database and name it "osticket"

![mstsc_GPs0JKMpSb](https://github.com/EMoniSmall/osInstall/assets/166156618/ea131dee-c5f7-4e0e-a5bf-19f027344041)

Step 5: On the osticket website, under MySQL Database, name it osTicket

Step 6: You can now enter your MySQL Username and Password. Click Install. 

<h2>Clean-up</h2>

Step 1: Once everything has installed, in a File Explorer, go to C:\inetpub\wwwroots\osTicket\Setup and delete the Setup Folder.

Step 2: Then go to C:\inetpub\wwwroot\osTicket\include and right-click os-config.php > Properties > Security > Highlight "Everyone" and click Edit. Uncheck everything except for Read & execute and Read. Apply. 

![mstsc_osNycPPXSz](https://github.com/EMoniSmall/osInstall/assets/166156618/be8238e2-7fbb-45a3-9141-23292acc8bf0)


<b>The initial setup and installation for osTicket is now complete!</b>
