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

- Size: `Standard_D4s_v3 - 4 vcpus, 16 GiB memory` (I recommend to choose one that has 2 vcpus & 8 GiB of memory but if you need more power, go with the on I selected.)
- Username: `labuser` (You can change this if you want, whatever is easy to remember.)
- Password: `osTicketPassword1!` (You can change this if you want, whatever is easy to remember.)

**We will creating a lot of usernames & passwords throughout this lab and what I do to keep track of everything so I don't forget is saving them in a notes app**

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

Next, we'll open Remote Desktop and paste the public IP address to login into the VM and click **Connect**.








