# Kali Linux Lab Setup on VirtualBox

**Author:** Sakinah Abubakar
**Date:** 30 October 2026

## Goal
Build a safe practice lab with Kali Linux (the attacker machine) inside VirtualBox, on a private network `10.0.0.0/24`.

## What I set up
- VirtualBox as the base
- Kali Linux 2026.3 (pre-built VirtualBox image)
- NAT Network `10.0.0.0/24`
- Kali IP address `10.0.0.2/24`
- Clipboard and drag-and-drop set to Bidirectional
- Windows Downloads folder shared with Kali
- Full internet access
- Snapshot of the finished VM

## Steps
1. Installed 7-Zip and VirtualBox.
2. Downloaded the Kali VirtualBox image from kali.org, extracted it, and added it with **Machine > Add**.
3. Created a NAT Network with prefix `10.0.0.0/24` (Ctrl+H > NAT Networks).
4. Set Kali's Adapter 1 to **NAT Network**, with Promiscuous Mode **Allow All**.
5. Set Shared Clipboard and Drag-and-Drop to **Bidirectional** (Settings > General > Features).
6. Shared the Windows Downloads folder with Auto-mount (Settings > Shared Folders).
7. Set the IP inside Kali to Manual: address `10.0.0.2`, netmask `24`, gateway `10.0.0.1`, DNS `8.8.8.8`.
8. Took a snapshot.

## How I checked it
Commands run in the Kali terminal:

```
ip a
ping -c 4 8.8.8.8
ping -c 4 google.com
ls /media
```

Results: the IP showed `10.0.0.2/24`, both pings had 0% packet loss, and `sf_Downloads` appeared in `/media`.

## Problems I fixed
- **"No bootable medium found":** the VM was empty. I used the pre-built Kali image instead.
- **Wrong network range:** VirtualBox defaults to `10.0.2.0/24`. I changed it to `10.0.0.0/24`.
- **Name field greyed out:** the adapter was on plain NAT. I switched it to NAT Network.
- **Kali had `10.0.0.3` instead of `10.0.0.2`:** I set the IP again with `nmcli`.

## Screenshots 
(Add after uploading the images to this repo.)


## Safety note
This lab is for learning only. Test only systems you own or have written permission to test.
