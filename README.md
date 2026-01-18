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

Now, you have to install the Rewrite Module `(rewrite_amd64_en-US)` from the **osTicket-Installation-Files** folder.

- Click: `(rewrite_amd64_en-US)`
- A prompt for Rewrite Module will pop up, just check the box **accept the terms in License Agreement** and hit **Install**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/0f3b62ad578763ed5a5e9b3445c1f3c6f16ff19e/17.png>

The installation for IIS URL Rewrite Module is complete, you can click **Finish**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/779e124a07609b2b688f9dcf0f5acaa94f0b951e/18.png>

## Step 7 - Create the directory C:\PHP

Now, your going to create a seperate folder to install `PHP` and we'll create this folder on the `C:\` drive.

- Right click on the file explorer icon and open a new tab.
- Navigate to the `Windows (C:)` by clicking the drop-down on `This PC`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/595ba6021ffa70b34ac362408c1ab5bb28a5363b/19.png>

Next, your going to create a new folder in the `C:\` drive named `PHP`.

- Right click within the `C:\` drive and hover over **New**, then click **Folder**.
- Name the new folder created `PHP`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/e7d27610e1c7e78ddf9b06bfe23e13b9dd0aadea/20.png>

Next, from the `osTicket Installation-Files` folder. We'll extract `php-7.3.8-nts-Win32-VC15-x86` zip file into the `C:\PHP` folder that you created.

- From the `osTicket Installation-Files`, right click `php-7.3.8-nts-Win32-VC15-x86` zip file and click **Extract All**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/8b0c698a811d6cb78f9b80dac7e4820ce3567058/21.png>

- A prompt will pop up and for the destination, you can type `C:\PHP` or click browse and navigate to `Windows (C:)` drive were the **PHP** folder is located and select the folder. You can click **Extract** to begin the process.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/0fc310d7bc4a7e1613b6eba6ad5590a341b9174f/22.png>

As you can see the files were successfully extracted into the **PHP** folder.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/5384714ecbea594d7a4d77fcc36719eaae312ba0/23.png>

## Step 8 - Install VC_redist.x86 (Microsoft Visual C++ Redistributable (x86))

Now, you have to install `Install VC_redist.x86` (Microsoft Visual C++ Redistributable (x86)) from the **osTicket-Installation-Files** folder.

- Double click `Install VC_redist.x86`.
- Check the box for **I agree the license terms and conditons**, then click **install**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/7c764ad8d06dc7a977faa5a104f2301e3562971d/24.png>

The installation for `Install VC_redist.x86` (Microsoft Visual C++ Redistributable (x86)) is complete, you can click **Close**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/62c17008319239aaa1d22aee5b1d8b74b25fbb91/25.png>

## Step 9 - Install MySQL (mysql-5.5.62-win32)

Now, you have to install `mysql-5.5.62-win32` from the **osTicket-Installation-Files** folder.

- Double Click `mysql-5.5.62-win32`.
- Click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/ff4bfed03d4a7018fb685729b1faa9a042bb2eb1/26.png>

- Check the box for **I accept the terms in the license Agreement**, then click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/19a13c9b027c1a658861e3b049710228154ae404/27.png>

- For the **Setup Type** Choose **Typical** and it should bring you to the next prompt or just click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/dfd9cb7c931ceb0a14107238f2961a3bce647bb5/28.png>

- Click **Install**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/87c97ef5e3289790b446b999b89c9737d7d9cd7d/29.png>

- Check the box for **Launch the MySQL Instance Configuration Wizard**. then click **Finish**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/fd8e57776ab98ab6488e5ab5270e3c70fc188058/30.png>

- Click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/2454ddfeed54ba5b8be9c4eec1e63525c18e15bb/30.png>

- Select **Standard Configuration**, then click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/b763e6801ade375add6fb9cc2ca756cfd812a5d8/32.png>

- You can bypass this prompt and click **Next**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/48f46a733b8f6156ee5e8adcb5757ada2c7fb300/33.png>

- This next step is really important and like I mentioned on **Step 1** to keep any passwords & usernames that you've created saved on a password manager app/software.

- New root Password: `ROOT` **(All Capital Letter)**
- Confirm: `ROOT` **(All Capital Letter)**
- Click **Next**

**This password is not ideal to use in the real world due to security safety, but for the sake of this demonstration and to keep things simple, you can use it**

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/f51f1ce3f0aea1e143483f4d881be8faccbcf4c9/34.png>

- Click **Execute**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/709dc0091d37fdb8dbb870d554f1ffc4849dd058/35.png>

The installation for `mysql-5.5.62-win32` is complete, you can click **Finish**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/0c70dbb97abd8f5d9c8fc9519278e1e8b9f78cbc/36.png>

## Step 10 - Open Internet Information Services (IIS) as an Admin & Register PHP from within IIS

Next, we're going to open IIS as administrator.

- In the search bar, type **IIS**. and you'll see `Internet Information Services (IIS) Manager`.
- Click **Run as administrator**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/0e449e86046a87870185217683da6a037fcf9323/37.png>

Next, from within the IIS Manager. We're going to open `PHP Manager`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/54c60c232827599016b6fb82bbb64c9c0d34676e/38.png>

Once inside PHP Manager, click the link `Register new PHP Version`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/8595ece5a877e0793deaff1ee68ab109446e7dfe/39.png>

A prompt will pop up and click the three dots.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/52a8bc535d282397f507cab8539cc5ba3c8bcb10/40.png>

Now, we're going to browse for the excutable file which is located on the **C:\ drive** in the **PHP folder** that we created in **Step 7** and this file is called `php-cgi`.

- Double click `php-cgi`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/68b6fbce023c2111df0975b3853e19fb1155130d/41.png>

As you can see the file is there and you can click **OK**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/9783fe35f66e6513041f7736d70f367d5861a13e/42.png>

Next, you have to reload the IIS to make sure the web server will load correctly and all the changes that were made take in effect.

- Right click `osTicket-VM`.
- Click **Stop**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/335501ca5afcbc457e6e3747904d676dba636c51/43.png>

IIS is stopped now and you can go ahead and start it again.

- Right click `osTicket-VM` again.
- Click **Start**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/f206a4f52bcc500fb2eaf9cfa28a1b41b40af2ab/44.png>

## Step 11 - Install osTicket-v1.15.8

Now, we're going to install osTicket.

- Open the `osTicket-Installation-Files` folder located on your desktop.
- Right click `osTicket-v1.15.8` and click **Extract All**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/cf39794d5943122aadd14024b8a8074e27d65b56/45.png>

Click **Extract**, we're going to unzip this file in the same `osTicket-Installation-Files` folder.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/5d1c12e6d7e6129d0ddb149315c5bdff39e92b0a/46.png>

As you can see the unzipped file is in the folder.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/ff027ca252d9f0dfad4b01b922240d52bfa1d6b2/47.png>

Next, inside the unzipped `osTicket-v1.15.8` folder. We're going to take the `upload` folder and move it to a new folder on the **Windows (C:)** drive called `www (c:\inetpub\wwwroot)`.

- Open a new file explorer.
- Go to the `Windows (C:)` drive.
- Double click `inetpub` file.
- Double click `wwwroot`, this is the folder were the `upload` folder will be moved too.

Now, we're going to drag the `upload` folder to the `wwwroot` folder.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/8953d1d2c2133f881cd0dcd551c49a4e5431fa18/48.png>

As you can see the `upload` folder is now in the `wwwroot` folder.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/b2873d83059d409e1b262d0c169f231b1f5b1c33/49.png>

Inside the `wwwroot` folder, we're going to rename the `upload` folder to `osTicket`.

- Right click `upload` folder.
- Rename: `osTicket` **(Rename it exactly how it is in the screenshot below)**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/2471fdb656f3dbddf9701442aab6b11851d7e6ee/50.png>

Now, we're going to open IIS Manager and reload IIS by doing the stop & start actions again like we did previously to ensure all the changes that were made take in effect.

- Right click `osTicket-VM`.
- Click **Stop**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/26a58e3ad5fa001bde8a194dd5655d17d4c2c4b0/51.png>

IIS is stopped now and you can go ahead and start it again.

- Right click `osTicket-VM` again.
- Click **Start**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/01ede261b4b0fad90189f2bf77d2fa25da697c52/52.png>

Next, we're going to open the osTicket installer.

- Click the drop-down next to `osTicket-Vm`.
- Click the drop-down next to `Sites`.
- Click the drop-down next to `Default Web Site`.
- Click on `osTicket`.
- Click `Browse *:80(http)` on the right side under **Manage Folder** to open the installer.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/de48b0edca3591e5fb2d5177df17d193a11df742/53.png>

Once you click  `Browse *:80(http)`, the osTicket installer will open on your web browser. **(The below screenshot is what it should look like)**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/89acd7735ec931c6fa4173e3dedef49b43c3c852/54.png>

Next, you'll notice some of the recommended extentions are not enabled which are the ones with the red (X). We will be going back to IIS Manager and enable these extentions.

- Within the `osTicket Home`, open `PHP Manager`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/1a72d4647ad98d7b671d0490885c935ac8ff5f4b/55.png>

Click the link **Enable or disable an extention**.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/e650e8344ba6cfc64ff6551ea0398a1489272315/56.png>

Next, we're going to enable the extentions that had the red (X) next to it. We can do this by locating the below extentions that are disabled and right click on each of them and click **Enable**. You can also click **Enable** on the right side of the screen under **Actions**.

- `php_imap.dll`
- `php_intl.dll`
- `php_opcache.dll`

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/121fd598f8b8e81317df6f0b0f32b49d0b1a72ce/57.png>

As you can see below the following extentions that were disabled are now enabled.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/d2bff8354f29b282af9ba66411295406c652d581/58.png>

Now, go back to the osTicket Installer web page and refresh. You can see the extentions that we enabled are checked off and there should be only two extentions that have a red (X) next to them.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/a19ea33e0ccb93702c7e8f394f05832c3cfceaa5/59.png>

## Step 12 - Rename ost-config.php

Now, we're going to rename a file on the Windows (C:) drive that osTicket uses for it's configuration.

- Open file explorer.
- Click on `This PC` then ` Windows (C:)`.
- Double click on `inetpub` folder.
- Double click on `wwwroot` folder.
- Double click on `osTicket` folder.
- Double Click on `include` folder.
- Find the PHP File that is named `ost-sampleconfig.php`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/f828cadc0fc2f474d132fddff0d0ace8b6c0a91f/60.png>

One you've found the PHP File `ost-sampleconfig.php`, we're going to rename it exactly like this `ost-config.php`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/ee67bd7a7bd2015015c85191e77fad302d019f3c/61.png>

## Step 13 -  Assigning permissions to the ost-config.php file.

Now, we're going to assign permissions to `ost-congif-php` file so that **osTicket** can make changes to the file on the backend.

- Right click on the `ost-congif-php` file.
- CLick on `Properties`.
- Within the `Properties` prompt click on `Security`.
- Then click on `Advanced`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/56e9317d322db4ae1551314f0d9ae23252a9c6be/62.png>

Once inside the `Advanced Security Settings for include` prompt, click on `Disable inheritance` then click on `Remove all inherited permissions from this object`. By doing this you'll be removing all the current permissions on this file.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/fb06d9a1fdebbd7a27262795e7cf7ae6476a1e04/63.png>

As you can see there are no permissions so next, click on `Add` then inside the `Permission Entry for include` prompt, click on `Select a principal`.

<img src=https://github.com/NickTech03/osTicket-Lab-Prerequisites-Installation-and-Validation/blob/8d642878719309be33e70f2c51cebeec925a6e58/64.png>

Once inside the `Select User or Group` prompt, were it says `Enter the object name to select`. type `Everyone` then click on `Check Names` and you'll noticed that it worked when the word is **underlined**. Then click on `OK`.

**Please note that this is not ideal for real world use, but to keep this lab simple you, this is fine to put.**

<img src=>















  











