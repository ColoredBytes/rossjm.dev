+++
author = "Joshua Ross"
title = "Building My Digital Playground 🛝"
date = "2024-04-17"
description = "Exploring the World of Homelabs!"
tags = [
    "Homelab",
    "software",
    "hardware",
    "virtualization"
]
showToc = true
+++

# Introduction


Welcome to Post Number 2. To start, around 2015, I got the itch to do a little more than just build computers and repair them. Don't get me wrong, I still do that, and it is still very much a thing I tend to enjoy, but finding the right people to build for or someone with the budget can be hard at times. I started to learn [Linux](https://en.wikipedia.org/wiki/Linux) around this time and was very fascinated with how it worked. It was a little hard at first since the person who showed me. It showed me exclusively how to use it via CLI and not a GUI. After getting the hang of how Linux worked, I bought a server from that same friend, which started the HomeLab journey and the transition to the first part of the lab.


# Software
## Proxmox


[Proxmox](https://proxmox.com/en/) is a Linux-based hypervisor using [KVM](https://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine) as its base, sprinkled with some special sauces from the maintainers of Proxmox. I've used this product for the whole time I've labbed. I started using it in 2016 after getting off the Ubuntu Server, which at the time was mostly just hosting my Plex Server. I found out the same friend mentioned before was using Proxmox. I decided to give it a try and instantly fell in love with it and how it worked. It was super simple for a beginner like me at the time to get started with making more than just a Plex VM. I did eventually move off Proxmox and went to **Hyper-V** but did not like how that worked exactly and wound up going back to Proxmox some years later after starting at my current job and started deploying loads. More VMs, including **Docker**, which is my next piece of software as it plays a huge role in my lab.


## Docker


[Docker](https://www.docker.com/) is a virtualization platform for software, but instead of creating full virtual machines, it uses containers to package and isolate applications along with their dependencies. I use this software daily and it is included in all my lab installs. It takes the hassle out of spinning up a VM, installing all the dependencies, and then configuring the application from there. With my Docker installs, these two pieces are a must for me when deploying the containers. I use the templates from [Pi-Hosted](https://github.com/novaspirit/pi-hosted) to easily deploy the containers, as they are already pre-configured and need minimal setup. I also use my own [Ez-Docker-Installer](https://github.com/ross-jm/Ez-Docker-Installer) script to install Docker and Portainer. If you're wondering what [Portainer](https://www.portainer.io/) is, It is a web interface that interacts with Docker to manage and deploy the containers. It can also manage Docker Swarm or Kubernetes as well. This is a very useful tool if you don't want to sit in the CLI for hours. With that being said, I don't think I could live without a docker in my lab.


## TrueNAS


[TrueNAS](https://www.truenas.com/) is Network Attached Storage OS, or (NAS) for short. This is pretty much the heart of my lab, besides Proxmox. I've used this for about a year now but did use FreeNAS's Predecessor beforehand. TrueNAS holds all my ISO's and backups, along with all my media. It shares out all the data using NFS shares and uses ZFS for the file system, which does wonders for redundancy and keeping the files small. I'm running [Scale](https://www.truenas.com/truenas-scale/) at the moment, which is great as it's running Debian Linux and has support for Docker, which, if I wanted to, would let me spin up containers on it that directly interact with the NAS daily, but at the moment I just have them on a VM as I like my NAS to just be a NAS. An important thing to point out is that TruenNAS is free, and if you don't feel like building your server, you can also buy some [units](https://www.ixsystems.com/) from them. They are on the pricier side but they are good quality.

# Hardware

## UniFI

[UniFi](https://www.ui.com) is the heart of Lab and the core networking stack. I currently run the following items.

- [UDM-SE](https://store.ui.com/us/en/pro/category/all-unifi-cloud-gateways/products/udm-se) --> This is the Firewall and Router.
- XG-16 --> This is my 10Gb SFP+ Switch. This is all the main Servers are connected to.
- US-24 --> This is my 24 Port 1Gb RJ-45 Switch and is in my office connecting all other devices on that side of my apartment.
- [USW Flex Mini](https://store.ui.com/us/en/pro/products/usw-flex-mini) --> This is my 5 Port Maanged 1Gb RJ-45 Switch. This is for all my IOT Devices in the LR and is connected to the UMD-SE via POE.
- [nanoHD](https://store.ui.com/us/en/pro/products/uap-nanohd) --> My Wi-Fi 5 AP that serves Wi-Fi to my whole place.

I started with the **US-24-** and **nanoHD** after getting recommendations from a friend and instantly was blown away by the performance. At the time of purchase of those two items, I was using [pfSense](https://www.pfsense.org/) as my firewall. If you're looking for a nice firewall please try **pfSense** it works wonders and I believe is great when you're getting into homelabbing and Networking. The **USW Flex Mini** I purchased about a year later as I needed more ports in my office. IT did well for the price and it was managed which is a huge plus. It being USB-C as well was great as I could use any cable that could power it or the adapter it came with. Fast Forward to **2024**, I Purchased the **UDM-SE** from the UniFi site and the **XG-16** from a friend. The addition of those two made the networking in my lab so much more responsive and in a sense healthier. It's about 2 months since the latest purchase and I have no regrets about it. It's Snappy, easy to use, and affordable in a sense. I could go on with talking about UniFi but this section will have to do. If you're interested in getting some UniFi equipment, I highly suggest their [Compact](https://ui.com/us/en/cloud-gateways/compact) line. It's highly affordable and easy to set up.

# Epilogue
Well, this is the end folks for this post. I had fun doing this one as I love talking about my home lab and what is inside of it. This mini data center keeps me sharp with my skills and is a fun hobby to indulge in as well. If you ever feel like you want to get into Labbing let me know or join my [Discord](htttps://jersh.tech/chat) and I'd be happy to talk more there as well.






