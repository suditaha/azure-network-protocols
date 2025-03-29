<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<br />


## 1 - Creating our Virtual Machines

<p>
<img src="https://i.imgur.com/kFD1wBL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created a Resource Group (RG-Network-Activities).
</p>
<br />

<p>
<img src="https://i.imgur.com/HdWgg60.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created a Windows 10 Virtual Machine (VM) (windows-vm). While creating the VM, I selected the previously created Resource Group. 
</p>
<br />

<p>
<img src="https://i.imgur.com/o285Ks5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
While creating the VM, I also allowed it to create a new Virtual Network (VNET) and Subnet and picked it as my virtual network.
</p>
<br />

<p>
<img src="https://i.imgur.com/ZrGmqy3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created a Linux (Ubuntu) VM. While creating the VM, I selected the previously created Resource Group.
</p>
<br />

<p>
<img src="https://i.imgur.com/NqmNkyA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
While creating the Linux VM, I also selected the previously created Virtual Network (VNET), as my Virtual Network.
</p>
<br />

## 2 - Observing ICMP Traffic

<p>
<img src="https://i.imgur.com/eyOWagQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I opened the Windows 10 Virtual Machine that I created (windows-vm) and installed Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/lhaZhEz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I opened Wireshark and started packet capture. Within Wireshark, I filtered for ICMP traffic only. I then retrieved the private IP address of the Ubuntu VM (linux-vm) and attempted to ping it from within the Windows 10 VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/ChmFEes.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After pinging the linux-vm's private IP, I then observed the ping requests and replies within WireShark. The ping request was successful as all packets were recieved by the linux-vm.
</p>
<br />

## 3 - Configuring a Firewall [Network Security Group]

<p>
<img src="https://i.imgur.com/JRbzqkg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiated a perpetual/non-stop ping from the Windows 10 VM to the Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
