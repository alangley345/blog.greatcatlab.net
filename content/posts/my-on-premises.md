---
title: "My On-Premises"
date: 2020-08-31T13:26:10-04:00
author: "Aaron Langley"
draft: false
---

## My On-Premises Setup

I wanted to take a minute to talk about what I have been running at home in addition to what I may stand up or teardown in the cloud. I've bounced around through several different technologies before settling on something that works for me and gives me a platform with sufficient resources to build whatever I see fit.

## Hardware

Currently at the time of writing this, I am running with everything packed into a 6U rack in my basement. Presently it is pretty full, and I think this is more that sufficient for the foreseeable future I get more familiar with optimizing pay-as-you-go services and serverless tools like lambda to ensure that everything shuts down when I'm not actively labbing. My hypervisor of choice has been Proxmox. It's open source, includes a backup scheduler, supports HA, multiple storage types, native container support via LXC, beta support for SDN, ACME certs and can be configured with Ceph as a software defined storage solution among other things. Besides Proxmox VE, the vendor also offers Proxmox Mail gateway and Proxmox Backup Server. [Proxmox](https://proxmox.com/en/)

### Proxmox-Cluster Equipment List

Cluster consists of the following:

* 2 x HP G2 600 mini with Core i3, 16 GB RAM and 250 GB SSD
* 2 x Lenovo M93p with Core i5, 16 GB RAM and 250 GB SSD
* 8 x Samsung 500 GB USB 3.0 SSD
* 2 x WD 1TB My Passport
* 2 x WD 2TB My Passport

This is all running a  4 node Proxmox cluster. It's not exactly performant, but I was able to put it together piece by piece and the flexibility of Proxmox and Ceph allowed me to build this up basically a few hundred dollars at a time.

<img class="special-img-class" src="/static/my-on-premises-1.jpg"/>

## Edge

My edge device is a Netgate branded MinnowBoard Turbot MBT-4220. This configuration came directly from Netgate and is no longer available Check out this page for specs if interested: [Netgate](https://store.netgate.com/MBT-4220-system.aspx) It has more than enough horsepower for my Spectrum connection and can handle VPN with IPS turned on, although my upload speed leaves a lot to be desired.

## Networking

My switch stack consists of 2 Cisco SG 350 series switches of the 10 port varieties. One has PoE and runs the OC200 controller and AP. These have a less than intuitive GUI and also have CLI functionality although not a robust as what the Catalyst series offers.

## Wireless

Wireless connectivity is broadcast from a TP-Link EAP 245 and their [OC200](https://www.tp-link.com/us/business-networking/ceiling-mount-access-point/oc200/) controller . They are more than enough for my needs and the AP supports broadcasting multi SSIDs with VLAN tagging. VLAN 1 bleeds to all VLANs on this device, effectively making it unusable if you are trying to get any kind of network separation. This was only discovered when I enable IPv6 RA on my VLAN 1 and saw VLAN 1 addressed showing up in my IoT VLAN.

## Raspberry Pis

You have to have a Raspberry Pi, or in this case two. Both have the stock raspberrian flavor of Debian installed and run Portainer as a frontend for docker containers.

## Miscellaneous

I also have some hardware that doesn't fit elsewhere but is worth bringing up here.

* Microtik Hex Gigbit router
* RIPE Atlas Probe gen. 4
* Magicjack adapter
