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

