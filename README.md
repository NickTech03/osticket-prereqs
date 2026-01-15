<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Lab: Prerequisites, Installation, and Validation</h1>

<h2>Introdution</h2>
osTicket is an open-source help desk platform designed to centralize and streamline customer support requests by converting emails, phone calls, and web form submissions into organized, trackable tickets.
</p>
Ticketing systems help IT teams organize and manage support requests in one central place. Instead of tracking problems through emails, phone calls, or messages, every issue is recorded as a ticket that can be assigned, updated, and monitored.
This makes sure no requests are missed, allows urgent problems to be fixed first, and helps IT staff work more efficiently. Ticketing systems also keep a history of all support activity, which improves accountability, security, and overall service quality.
</p>
This is the **FIRST** part of a three part osTicket Lab and in this repository, we'll go over a 

<h2>Environments and Technologies Used</h2>

<h2>Operating Systems Used </h2>

<h2>List of Prerequisites</h2>

# Installation Steps/Walkthrough

---

## Step 1 - Create an Azure Virtual Machine 

Start by creating a resource group, you can make one while inside the creation of the virtual machine.

- Click: **Create new**
- Name: `osTicket`

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/ee6e9972f245c3416bbed8e45481a9f1d6bce695/1.png/>

 We can move onto naming our VM, selecting perfered region and image options.

- Virtual machine name: `osTicket-VM` (You can use a different name, this is the name I choose that's related to this lab.)
- Region: `(Canda) Canada Central` (I chose this region as this is closest to me, please choose a region that is local to you.)
- Image: `Windows 11 Pro, version 25H2 - x64 Gen2` (For this demonstration, I went with the following image. I've also used `Windows 10 Enterprise N, version 22H2 - x64 Gen2` which works fine as well. I prefer doing this lab on Windows 11, as modern day computers are using this Operating Systems.)

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/410bce54b67e098d20e800ed1df3fe7142c97781/2.png>

We can move onto selecting the VM size and make a username & password.

- Size: `Standard_D4s_v3 - 4 vcpus, 16 GiB memory` (I recommend to choose one that has 2 vcpus & 8 GiB of memory but if you need more power, go with the one I selected.)
- Username: `labuser` (You can change this if you want, whatever is easy to remember.)
- Password: `osTicketPassword1!` (You can change this if you want, whatever is easy to remember.)

**We will be creating a lot of usernames & passwords throughout this lab and what I do to keep track of everything so I don't forget is saving them in a password manager app/software. (Please note that due to security reasons and unwanted threats on the internet, it is not good practice to keep passwords on a notes app or plain/readable text document)**

**Click the check box to confirm licensing**, then click **Review + create**

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/e1d9a1dd740ba0759b84d465478defd8e2186b15/3.png>

We can move onto finalizing the creation of the VM. 

As you can see the validation is passed. All you have to do is click **Create** and the VM is ready to go!

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/e02dd4ea5d96cc9e3783ef5a45d532b595345aa1/4.png>

---

## Step 2 - Log into the VM using Remote Desktop Connection

Now we can go ahead an log into the VM that we created using Remote Desktop Connections (RDP).

We'll start by copying the **Public IP Address** which is located on the VM home page.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/948517611721921761a1ad79195540fad104d94b/5.png>

Next, we'll open Remote Desktop and paste the public IP address to login into the VM and click **Connect**. (for the username section, use the same username used when creating the VM.)

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/2e1dd38c45437b835310bfa32066f2f71fa89373/6.png>

Now login with password you used to created the VM then click **OK**.

 - Username: `labuser`
 - Password: `osTicketPassword1`

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/da19a9cd86e180cfad4ef59e0bcf9809bc0f84f1/7.png>

This prompt will pop up, click **Yes** to continue.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/3547c7e167fc0d0784eed3f187e979218833d381/8.png>

---

## Step 3 - Within the VM download osTicket installation files

Now that you've gotten logged into the VM, were going to download the required installation files below for osTicket and extract the file to the desktop.

- Download: https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD
- Click: **Download anyway**

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/a7a70736f0fdc98749222503a9f2cde8ae8e0e2c/9.png>

Once extracted onto the desktop you should have a folder containing all the required installation files for osTicket.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/e3f4d7446cf4c52c982d9318a4dea31948db6a18/10.png>

## Step 4 - Install / Enable IIS in Windows (WITH CGI)

Now you have to install / enable IIS in Windows (WITH CGI) using the following steps. (We can bypass some searching by typing **windows features** in the search bar.

- Windows search bar: `windows features`
- Click: **Turn Windows features on or off**

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/9c8544e328081821c11eb4b57036120a8a6fe09d/11.png>

Once windows features is open, you now have to do the following steps.

- Click the box next to `IIS (Internet Information Services)` and click the (+) next to it, another set of drop-downs will show.
- Click the (+) next to `World Wide Web Services` and click the (+) next to `Application Development Features`, another set of drop-downs will show.
- Check: `CGI`, then hit **OK**. 

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/f61790213161c494ad34d7f2f7d6eabeeaf80101/12.png>

Now the web server will be installing and after it's finished you can hit **Close**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/6c42ba7ffd8bab6aec26753b752c371ae85ddfb2/13.png>

## Step 5 - Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0)

Now you have to install PHP Manager `(PHPManagerForIIS_V1.5.0)` from the **osTicket-Installation-Files** folder that you downloaded previously.

- Open `osTicket-Installation-Files`
- Click: `(PHPManagerForIIS_V1.5.0)`
- A prompt for PHP Manager will pop up, just click **Next**

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/7364c0107027432aace6591460438ed688ee653b/14.png>

Next, click **I Agree** and then **Next** on everything else afterwards.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/65aaec3af405a6e1f6e95e98ec9a78b65bbb58fa/15.png>

The installation for PHP Manager is complete, you can click **Close**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/7f2d56d59bd1336d6110d25ce53d1aa273abd9d9/16.png>

## Step 6 - Install the Rewrite Module (rewrite_amd64_en-US)

Now you have to install the Rewrite Module `(rewrite_amd64_en-US)` from the **osTicket-Installation-Files** folder.

- Click: `(rewrite_amd64_en-US)`
- A prompt for Rewrite Module will pop up, just check the box **accept the terms in License Agreement** and hit **Install**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/0f3b62ad578763ed5a5e9b3445c1f3c6f16ff19e/17.png>

The installation for IIS URL Rewrite Module is complete, you can click **Finish**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/779e124a07609b2b688f9dcf0f5acaa94f0b951e/18.png>

## Step 7 - Create the directory C:\PHP

Now, we're going to create a seperate folder to install `PHP` and we'll create this folder on the C:\ drive.

- Right click on the file explorer icon and open a new tab.
- Navigate to the `Windows (C:)` by clicking the drop-down on `This PC`.

<img src=>














  











