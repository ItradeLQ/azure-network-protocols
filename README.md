<p align="center">
<img src="https://i.imgur.com/0rS4fzT.png?1" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Two Azure Virtual Machines</h1>
In this tutorial, various network traffic to and from Azure Virtual Machines was observed with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command-Line Interface Tools (CLI)
- Network Protocols [ICMP, SSH, DHCP, DNS, RDP, HTTP(S)]
- Wireshark (Network Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

Observe the following:
- Internet Control Messaging Protocol (ICMP) Traffic
- Secure Shell Protocol (SSH) Traffic
- Dynamic Host Configuration Protocol (DHCP) Traffic
- Domain Name System (DNS) Traffic
- Remote Desktop Protocol (RDP) Traffic

<h2>Actions and Observations</h2>

1. In this demonstration two virtual machines will be created using Microsoft Azure. One Virtual Machine (VM) will be used for Ubuntu Linux, and the other Windows 10 as its operating system (OS). For the Virtual Machines sizes, I went with 2vcpus | 16GiB for more processing power. Once both VMs are set-up, go ahead and login to the Windows 10 version. Download and Install [WireShark](https://www.wireshark.org/download.html). 

<a href="https://imgur.com/NjAe6T7"><img src="https://i.imgur.com/NjAe6T7.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/xAFnukb"><img src="https://i.imgur.com/xAFnukb.png" title="source: imgur.com" /></a>



Open WireShark and search for ICMP Traffic only. This traffic will display the relay request and delivery, also known as "ping". We will be able to see how many packets are requested and recieved. Wireshark can then be used to inspect the packets of data. 

<a href="https://imgur.com/y9ZjdRI"><img src="https://i.imgur.com/y9ZjdRI.png" title="source: imgur.com" /></a>

2. Observation of SSH Traffic. Filter for SSH Traffic in WireShark. From the Windows 10 VM, "SHH into" the Ubuntu VM. This can be done by using the command, "SSH username@ipaddress". In my case, SSH cclabuser@10.0.5 , then we will see that WireShark immediately send the SSH packets between the two VM. 

<a href="https://imgur.com/isSdOyc"><img src="https://i.imgur.com/isSdOyc.png" title="source: imgur.com" /></a>


3. Obeserve DHCP Traffic, DHCP is Dynamic Host Configuration Protocol which operates on ports 67 and 68. The main function of DHCP is to assign different devices their IP-Address. Filter for DHCP in WireShark. We can attempt to issue a new IP address to our Windows 10 VM by using powershell and entering the line "ipconfig /renew". Now, inspect WireShark for this traffic. 

<a href="https://imgur.com/xuoVhQY"><img src="https://i.imgur.com/xuoVhQY.png" title="source: imgur.com" /></a>

4. Observe DNS Traffic, once again, filter for DNS. In PowerShell, use the command "nslookup" to see what www.google.com or most of any website IP addresses are. Now, inspect WireShark and the traffic it is capturing here. 

<a href="https://imgur.com/Y0r57q2"><img src="https://i.imgur.com/Y0r57q2.png" title="source: imgur.com" /></a>

5. Observe RDP Traffic and filter for RDP. We can also do this by entering "tcp.port == 3389" in WireShark. Traffic constantly flowing, showing a live stream of packets from one computer to another. That's because both VMs are connected via RDP and any interaction will be recorded. 

<a href="https://imgur.com/9gbvRb1"><img src="https://i.imgur.com/9gbvRb1.png" title="source: imgur.com" /></a>


We've reached the end of this exciting tutorial. In the [next tutorial](https://github.com/ItradeLQ/network-file-shares-and-permissions), the focus will be setting up Network File Sharing and Permissions on the host. Since these are interlinked labs, it is best not to destroy the Resoruce Group and virtual machine created in this tutorial.
