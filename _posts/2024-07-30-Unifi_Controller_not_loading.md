---
title: Unifi Controller installs without web GUI
description: Unifi Problems
date: 2024-07-30 13:00:00:01 +/-0000
categories: [Unifi, Troubleshoot]
tags: [virtual,unifi]     # TAG names should always be lowercase
toc: true
comments: active
ping: true
---

Ubiquiti's Unifi Wi-Fi line is the first real enterprise system I got my hands on.  Before Ubiquiti came into the picture, I spent countless hours programming individual Netgear Prosafe Wireless devices for events.  Thankfully the invention of a controller occured, and now all AP's could be managed from a single computer.

When I first started using the Unifi controller, we had installed on a laptop. I won't dare say what shows we did that for.  We then moved to installing them on MicroServers. This helped because at the time it also served as our dhcp server.  We had to use servers at each site because Layer 3 adoption was not available and the controller had to be onsite.  Thankfully Ubiquiti continue to upgrade and improve there product, and is now capable of running in the cloud.

As I changed jobs, I adopted a controller that was very sluggish. It would seem that the controller would need to be rebooted on a daily basis.  The site probably had 300 access points at the time and running on a windows server virtual machine.

Long story short I know put all of my controllers on Linux:Ubuntu with obvious help from Willie Howe's Youtube channel.  Time and unifi versions had past. I found that the controller could handle more than 300 now, but was beginning to be sluggish with over 600 access points.  After some discussion with some of the developers, they had mentioned that Windows has a hard time with accelerating something that Linux can do easily.  I'm not as familiar with linux as I'd like to be, but the good thing about running the Unifi controller on a windows hyper-v is that if you break it, you can revert back if you've taken a snapshot.

While trying to install the Unifi controller on Ubuntu I came into a couple of snags.  Recently I needed to re-install the controller at my house on a virtual machine. I had sadly forgotten the steps. It makes me miss just double clicking with Windows .exe files. I do have to say though, that it feels gratifying to know you can install something in command line.  Even if someone tells you what commands to type.  I followed Willie Howe's very easy 3 step process.  The package would install but the website url would never load.  I was at a loss for a few hours.  I probably setup and deleted 6 virtual machines trying to create the cleanest minimalist install I could.  What Willie and others failed to have in their install process is to tell us about Java.  Yes Java.

Java was the vain of my existence at my previous employer.  Look into heap sizes and manually configure how much java can take in resources to run. With 600+ access points, the controller would only use 4gb of ram. I was told to increase heap sizes and make a few other changes, that I wish I remembered.




Steps - Currently I have only setup this on Microsoft Hyper-V

Virtual Machine Setup - Reccommended Setup from Unifi
Setup A Hard Disk - I used 30gig
Setup the Virtual Machine
2 Gigs of ram
Install Ubuntu
Install commands

2. Make sure your device is up to date

```text
sudo apt-get update && sudo apt-get upgrade
```

Install Java

```text
INSERT CODE HERE
```

Download Unifi Controller (example)

```text
wget https://dl.ubnt.com/unifi/5.10.17/unifi_sysvinit_all.deb
```

List the download so you know it downloaded and what the file name is.

```text
ls
```

Unpackage and install the file (Enter password when prompted)

```text
sudo dpkg -i unifi_sysvinit_all.deb
```

Install the dependencies (Press Y when prompted)

```text
sudo apt-get -f install
```



If you have an older install of the controller you will need to remove the old file.

```text
username@Unificontroller:~$ 'ls'
unifi_sysvinit_all.deb
username@Unificontroller:~$
```

To remove the file you will need to send the following command:

```text
sudo rm unifi_sysvinit_all.deb
```

I hope this helped you. Let me know if you have had any problems with your Unifi install or any cool projects with Ubiquiti's gear.  I've recently been working on setting up Guest Networks, to help separate my family network from visitors that ask for their Wifi Password. When was the last time you changed your Wi-Fi password?