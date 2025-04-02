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
<img src="https://i.imgur.com/iOuiFRS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Opened the Network Security Group that the Ubuntu VM is using and disabled incoming (inbound) ICMP traffic by creating a new security rule.
</p>
<br />

<p>
<img src="https://i.imgur.com/hqTmTal.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in the Windows 10 VM, I observed the ICMP traffic in WireShark. Notice how the requests are starting to time out (no response found).
</p>
<br />

<p>
<img src="https://i.imgur.com/tDQxWuo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I also observed the ICMP traffic in the command line's ping activity. Notice how the requests are starting to time out here too (Request timed out).
</p>
<br />

<p>
<img src="https://i.imgur.com/JseDbYv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Re-enabled ICMP traffic for my Ubuntu VM via the Network Security Group settings by deleting the security rule I previously created.
</p>
<br />

<p>
<img src="https://i.imgur.com/ixsxdV3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in the Windows 10 VM, I observed the ICMP traffic in WireShark and the command line Ping activity (it started working again ✅).
</p>
<br />

## 4 - Observing SSH Traffic

<p>
<img src="https://i.imgur.com/N8w9j7G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, I started a packet capture up and filtered for SSH traffic only. From the Windows 10 VM, I connected via SSH to the Ubuntu Virtual Machine (with its private IP address, 10.1.0.5). To do this, I typed : ssh suditaha@10.1.0.5 in PowerShell.
</p>
<br />

<p>
<img src="https://i.imgur.com/6mManfu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I typed commands such as (id, hostname, etc) into the linux SSH connection and observed SSH traffic spam happening live in WireShark everytime I typed a keystroke or a command.
</p>
<br />

## 5 - Observing DHCP Traffic

<p>
<img src="https://i.imgur.com/jKr947X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, I filtered for DHCP traffic only. From my Windows 10 VM, I attempted to issue my VM a new IP address by making a new notepad file called "dhcp.bat" with the text "ipconfig /release" & "ipconfig /renew" written in it in order to force the Windows 10 VM to release its current IP address and request a new one from the DHCP server.
</p>
<br />

<p>
<img src="https://i.imgur.com/N5Cgcfj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I opened PowerShell as admin and ran the dhcp.bat file, then I saw the DHCP traffic in Wireshark showing the full DHCP lease renewal process including Release, Discover, Offer, Request, and ACK.
</p>
<br />

## 6 - Observing DNS Traffic

<p>
<img src="https://i.imgur.com/QZH6qjl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, I filtered for DNS traffic only. From my Windows 10 VM within the command line, I used nslookup to see what disney.com’s IP address is. I then observed the DNS traffic being showN in WireShark.
</p>
<br />

## 7 - Observing RDP Traffic

<p>
<img src="https://i.imgur.com/bN6LxN5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, I filtered for RDP traffic only (tcp.port == 3389). I then observed the immediate non-stop spam of traffic that happened.
</p>
<br />
