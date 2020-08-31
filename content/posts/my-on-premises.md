---
title: "My On-Premises"
date: 2020-08-31T13:26:10-04:00
author: "Aaron Langley"
draft: true
---

# My On-Premises Setup
I wanted to take a minute to talk about what I have been running at home in addition to what I may stand up or teardown in the cloud. I've bounced around through several different technologies before settling on something that works for me and gives me a platform with sufficient resources to build whatever I see fit. 

## Hardware 
Currently at the time of writing this, I am running with everything packed into a 6U rack in my basement. Presently it is pretty full, and I think this is more that sufficient for the forseeable future I get more familar with optimizing pay-as-you-go services and serverless tools like lambda to ensure that everything shuts down when I'm not actively labbing. My hypervisor of choice has been Proxmox. It's opensource, includes a backup scheduler, supports HA, multiple storage types, native container support via LXC, beta support for SDN, ACME certs and can be configured with Ceph as a software defined storage solution among other things. Besides Proxmox VE, the vendor also offers Proxmox Mail gateway and Proxmox Backup Server. [Proxmox](https://proxmox.com/en/)

### Proxmox-Cluster Equipment List
Cluster consists of the following:

* 2 x HP G2 600 mini with Core i3, 16 GB RAM and 250 GB SSD
* 2 x Lenovo M93p with Core i5, 16 GB RAM and 250 GB SSD
* 8 x Samsung 500 GB USB 3.0 SSD
* 2 x WD 1TB My Passport
* 2 x WD 2TB My Passport

This is all running a  4 node Proxmox cluster. It's not exactly performant, but I was abble to put it together piece by piece and the flexibility of Proxmox and Ceph allowed me to build this up basically a few hundred dollars at a time.

![My Proxmox Cluster](https://blog.greatcatlab.net/static/my-on-premises-1.jpg)

## Edge
My edge device is a Netgate branded MinnowBoard Turbot MBT-4220. This configuration came directly from Netgate and is no longer available Check out this page for specs if interested: [Netgate](https://store.netgate.com/MBT-4220-system.aspx) It has more than enough horsepower for my  Spectrum connection and can handle VPN with IPS turned on, although my upload speed leaves a lot to be desired.

## Raspberry Pis
You have to have a Raspberry Pi, or in this case two. Bother have the stock raspberrian flavor of Debian installed and run Portainer as a frontend for docker containers. 