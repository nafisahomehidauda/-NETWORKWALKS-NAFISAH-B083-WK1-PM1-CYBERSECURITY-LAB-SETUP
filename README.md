📌 Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

🎯 Objectives
The main objectives of this project are to:

Install and configure VirtualBox.
Install/import Kali Linux as a virtual machine.
Create a private NAT Network for the cybersecurity lab.
Configure network connectivity for Kali Linux.
Assign a consistent IP address to the Kali VM.
Verify network connectivity and DNS resolution.
Take a clean VM snapshot for recovery.
Document the complete setup process.
Prepare the environment for future cybersecurity projects.
🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

* Network reconnaissance
* Port scanning
* Vulnerability assessment
* Packet analysis
* Web security testing
* Exploitation practice
* Security-tool experimentation

⚠️ Important: This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.


🪜 Lab Setup Procedure

Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.

Tool: 7-Zip

Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration: 
Network Name: NatNetwork 
IPv4 Prefix: 10.0.0.0/24 
DHCP: Enabled 
IPv6: Disabled

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1

Attached to: NAT Network

Network:     NatNetwork

Adapter Type: Intel PRO/1000 MT Desktop

Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

IP Address: 10.0.0.2

Subnet Mask: 255.255.255.0

Gateway: 10.0.0.1

DNS: 8.8.8.8, 10.0.0.1

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

Fresh Kali after installation- Network Setup

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.


Problems Encountered & Solutions

Problem  1. Virtualization Error while setting up Kali Linux lab in VirtualB0x

After trouble shooting, I discovered that Intel (R) the Virtualization hardware and the Intel (R) VT-d Feature was disabled in BIOS setting.
I enabled it, restarted the computer and VirtualBox was able to run Kali Linux successfully.


Problem 2. Internet Connectivity After Static IP Configuration

After manually configuring the IPv4 settings,I Lost Internet connectivity and had to check the Kali/NetworkManager configuration.
The problem was from the NetworkManager configuration.

One workaround I used during this lab was:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

The network connection was then restarted/rebooted and connectivity was tested again.


Problem 3. BASIC/EXPERT MODE

I couldn't find the Network option after clicking tools in virtualBox
I found out it was running on the basic mode. After switching it to expert mode every other step worked fine.


What I Learned
Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

4. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

Security & Ethical Use
This laboratory is intended strictly for education purposes only.

🔗 Tools & Resources
7-Zip: https://7-zip.org/download.html
VirtualBox: https://virtualbox.org/wiki/Downloads
Kali Linux: https://kali.org/get-kali

