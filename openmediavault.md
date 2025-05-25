# Getting Started with OpenMediaVault on Raspberry Pi

If you want to host a file server on your Raspberry Pi, OpenMediaVault (OMV) is a great choice that will make your life easier. It’s a web interface to manage everything on your devices: from your storage drives (detection, mounting, formatting) to your file sharing (creation, permissions, etc.). I’ve used this distribution a lot, and in this article, I’ll explain how to use it on a Raspberry Pi.

OpenMediaVault is a network-attached storage (NAS) solution that can be installed on any Debian-based distribution, such as Raspberry Pi OS Lite. It can be used to host and configure a file server via a web interface in a few clicks.

This article will explain each step in detail, so you can use the software on your device and easily create a file share at home.

## Table of Contents

* Why Do You Need OpenMediaVault?

* Recommended Hardware to Host a File Server at Home

* Install the Base System for OpenMediaVault

* OpenMediaVault Installation on a Raspberry Pi

* First Steps with OpenMediaVault

If you’re new to Raspberry Pi or Linux, I’ve got something that can help you right away!  Download my free Linux commands cheat sheet – it’s a quick reference guide with all the essential commands you’ll need to get things done on your Raspberry Pi. Click here to get it for free!

Want the best experience? Become a premium member for ad-free browsing, access exclusive content, and ask questions in our private forums. Your membership helps support the site!

## Why Do You Need OpenMediaVault?

As explained in the introduction, the main goal of OpenMediaVault (OMV) is to install a file server and give you a nice web interface to manage it. But this tool doesn’t reinvent the wheel.

Basically, it will install the main components of a NAS file server and provide an interface between you and the configuration file (a bit like Webminor Cockpit, but dedicated to the file server, and slightly better I think).

You can absolutely do the same thing by using Samba and a few other packages, but the installation, configuration, and maintenance are way more complicated (I have a complete guide about that if you want, even if it’s just to take a look at the difference).

In my job, I even switched from OpenMediaVault to native Debian on some servers (because I needed to update the base system, but OMV wasn’t available with the latest version at the time). I no longer had the web interface, but the Samba configuration remained the same and the file share still worked.

## Recommended Hardware to Host a File Server at Home

* Fast & big SD card: For a file server, I recommend a big SD card (at least 128 GB) so you can store everything on it. This one is the best model available right now (and often available at a discount).

* Raspberry Pi: The Raspberry Pi 5 and Pi 4 are both supported by OpenMediaVault. There’s no need to think more about it; get a Pi 5 or a Pi 4 with at least 4 GB, you won’t regret it.

* SSD drive: If you expect more performance, a Raspberry Pi and an SSD allow you to run systems really fast and get the best response time when opening your files. My favorite model is this one, and SSD drives are now really affordable, go for it (USB adapter included).

You’ll need two storage drives anyway, so a combination of an SD card (or USB stick) for the system and the external USB drive (SSD or not) is great for this project.

## Install the Base System for OpenMediaVault

Historically, OpenMediaVault was a separate Linux distribution. You had to install the image from scratch on a new server (or Raspberry Pi). With the latest versions, OpenMediaVault is now a simple package you can install on any Debian-based distribution, which is way better for us.

The first step is to have or install your operating system on a Raspberry Pi. For this tutorial, I’ll be using Raspberry Pi OS Lite. But it should work with other distributions, at least those based on Debian (Ubuntu, DietPi, etc.).

Warning: it looks like OpenMediaVault is no longer supporting installations on a system with a desktop environment. So make sure to use Raspberry Pi OS Lite for this project, or you’ll get an error like: This system is running a desktop environment! Please use a Lite version of the image or do not choose to install a desktop environment.

Whatever the case, make sure that you have:

* Installed a Debian-based distribution.

* Configured Internet access. Take note of your Raspberry Pi’s IP address. You’ll need it later on (read this tutorial if you don’t know what I’m talking about).

* Updated the system: sudo apt update && sudo apt upgrade

Setting up SSH access on your Raspberry Pi might be a good idea if you have another computer to follow this tutorial from. This way, you can just copy and paste the commands I give you here and access the web interface from your computer.

## OpenMediaVault Installation on a Raspberry Pi

Here are the main steps to install OpenMediaVault on Raspberry Pi OS:

* Use the installation script to install all dependencies and complete the basic configuration.

* Access the web interface to create your custom server.

We’ll now learn how to do these steps in detail next.

Note: If you want to see all these steps in action, I have a video lesson available for community members. You can join here and watch it directly if you are interested (with 10+ other lessons for Raspberry Pi and many other benefits).

## Install OpenMediaVault

As mentioned previously, OpenMediaVault can now be installed like a simple package. It’s not available in the default repository, but you can install it by using their installation script. Here’s how to get it in one command line:

wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash

It will install everything you need without asking additional questions during the installation. The script will also reboot your Raspberry Pi when it’s done.

I tested it on Raspberry Pi OS Lite (Bookworm, 64-bit), to check if the latest version was supported, but any version should be fine.

Note: Older Raspberry Pi models, like the Raspberry Pi 1 are not supported, and the installation will fail with this kind of error:

This RPi1 is not supported (not true armhf). Exiting…

It’s not recommended to try with this model or the Pi Zero, as they will be very slow anyway. Try to get a newer board.

Are you a bit lost in the Linux command line? Check this article first for the most important commands to remember and a free downloadable cheat sheet so you can have the commands at your fingertips.

## Access the Web Interface

After the system reboots, you should be able to access the web interface directly:

* Open a web browser on your computer.

* Type your Raspberry Pi addresswith the HTTP prefix, so for example: http://192.168.1.100  You can also use the Raspberry Pi hostname if you know it: http://raspberrypi.local

*  These are just examples; you may have changed these settings in Raspberry Pi Imager during installation or after installation by using the hostname command.

* The web interface will appear with a login prompt:

* Enter the default credentials to log in for the first time:

    * Login: admin

    * Password: openmediavault

* You can change these credentials once logged in, and I’ll show you how in the next section.

You’ll then gain access to the full interface. The dashboard needs to be configured, but you have a left menu with all the features included in OpenMediaVault.

## First Steps with OpenMediaVault

The goal here is not to give a detailed guide on how to use OpenMediaVault (there is the official documentation for that). Instead, I want to guide you with the first steps that anyone will have to follow, whatever the exact project is. I hope it will be useful and save you time.

### Change the Administrator Password

For security reasons, it’s always a good practice to change the default credentials as soon as possible after the installation. Even if it’s just a small server at home, default passwords will be tested directly if someone finds that you are using OpenMediaVault or a Raspberry Pi.

To change the default OpenMediaVault password:

* Click on the “User Settings” icon in the top-right corner.

* A menu shows up, click on “Change Password”:

* Enter the new password twice, and click on “Save” to apply your changes.

You can also use the same menu to switch to another language if needed.

Good, you can now move forward with your project!

### Dashboard Configuration

By default, the home page is empty, and you’ll get a message explaining what to do: “The dashboard has not yet been configured. To personalize it, please go to the settings page.”

Just click on the link to configure the widgets you want to add to this page. The dashboard is really well done—you can have a quick overview of the hardware usage (CPU, memory, network) and your current configuration (enabled services, shares, file systems, etc.).

For some of the widgets, you have the choice between “table” and “grid” options. Pick either one since they’re just different designs. Grids have colors and graphs, while tables are more traditional.

Table (on the left) vs grid (right)

### Mount Your Storage Drives

The serious part begins when you try to add your storage drives. This was already the case a few years ago when I first tried OpenMediaVault, but I feel it’s not very intuitive. The interface helps, but there are several steps and if you forgot one step, it won’t work.

Anyway, mounting and formatting the disk is not that complicated, so let’s start with it.

I’m testing this by using the Argon One case, with a 1Tb M2 SSD in the case. OpenMediaVault is installed on my favorite USB key (but you can use an SD card), and I will show you how to mount the SSD, format it, and create a file share on it. The steps should be similar if you use a USB drive or even a HAT with several SATA drives.

* First, make sure your data drive is detected. Go to Storage > Disks to list all of them:  In my case, both are detected (USB+SSD), and I’m interested in the first one (/dev/sda).

* Optional: Go to “Software RAID“ if you have several disks and want additional security.  For example, if you have two drives, you can configure a mirror, so that if one disk is corrupted, the other one will save your life (and files).  This setup is particularly complicated to do via command line and where OMV is really useful.

* Then format your disk with EXT4. I tried with a FAT partition created on my computer but ran into many issues, so I guess OMV works best with a Linux file system. Go to Storage > File Systems and click on “Create”. You may need to mount it first. Choose your device (/dev/sda in my case) and the file system (EXT4 works fine).

That should be enough. In a few steps, new data storage is now available.

### Create Your First Share

This is where I got a bit lost in the process because there are several locations in the left menu to configure the “share” folder:

* In Storage > Shared folders: you create a folder and can give permissions to it for your users. But it doesn’t mean you can access it from another computer. It’s only a local folder.

* In Services > SMB/CIFS > Shares: that’s where you configure a shared folder, that can be accessed from another computer.

So, start by creating a new folder in Storage > Shared folders. Set a name (“share” or whatever), select the file system you just created (/dev/sda1 in my case), and pick the default permissions. This is just for local access, so it doesn’t really matter for now.

Then, go to Services > SMB/CIFS. In the “Settings” submenu, make sure the service is enabled. If not, check the “Enabled” box and click Save.

You can now open the “Shares” submenu, and create the shared folder.

The form might feel overwhelming, but you can keep the default values in most cases. Select the shared folder created in the previous step, and everything else is optional. Just change what applies to your case.

If you prefer not to bother with user passwords and permissions, set the “Public” field to “Guests allowed.”

Once all the steps are completed, the new folder is listed under Services > SMB/CIFS > Shares:

Now you can access it via your file explorer from a computer. On Windows, use \\IP_ADDRESS and on Linux/Mac, it should be something like smb://IP_ADDRESS.

If guests aren’t allowed, you’ll be asked for a login and password. Keep reading to learn more about this.

### Share Permissions Management

That’s another step that is hard to configure when there is no web interface. So OMV is pretty handy if you want to give different permissions to different users.

The best practice is to use users and groups to manage permissions to your shared folders:

* Create a different group for each level of access. Maybe it’s “admins” and “users”. Or perhaps it’s one group per shared folder. Find what is best depending on your project. For a simple share at home, one group named something like “share_access” might be enough, to explicitly configure who can access the shared folder. Go to Users > Groups to create the corresponding group(s).

* Then create one user for everyone. In general, you’ll create one username for each individual, but you can also have more if you have some scripts or apps connecting to this device (a backup service, for example).  Go to Users > Users to create the corresponding user(s). Make sure to add them to the correct groups you created previously.

Once you have created at least one user and group for yourself, we can move on and configure the shared folder permissions:

* Get back to “Groups” and select the group you want to give access to your shared folder.

* Click on the privileges icon in the upper bar:

* You can now choose which permissions to give for each shared folder you created:

    * Read/Write: full access to the files in this folder.

    * Read only: can open all files, but not edit them.

    * No access: can’t open any file.

You can do the same thing in the Users submenu. But it’s generally best practice to use groups so that it will work directly when you add new users to this group in the future.

### Using Plugins With OpenMediaVault

The last feature I want to introduce is the additional plugins. OpenMediaVault is generally used to host a basic file server, which is why I mainly wrote about it in this article. But you can easily install new plugins, to enhance your experience and add new features to your file server.

You can for example add a plugin to enable an Antivirus or file encryption on your system. To do this, go to System > Plugins. You’ll get a list of the supported plugins. Just click on the one you are interested in, and click on “Install” to install it automatically.

After the installation, the plugin will generally be available in a submenu, with additional settings to configure it. Here is an example with the Antivirus plugin (ClamAV):

Obviously, you can always use SSH and install ClamAV on your Raspberry Pi manually. But the web interface to manage it is appreciable.

I hope this guide has been useful to get started with OpenMediaVault on your Raspberry Pi. Please don’t hesitate to check their documentation for more details (once installed, using a Raspberry Pi or a $10k server doesn’t change anything in the interface), and contact me if you have any additional questions.
