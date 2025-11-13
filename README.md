<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 11 (Domain Controller)
- Linux (Ubuntu Server 20.04)

<h2>High-Level Steps</h2>

- Log in to Remote Desktop Protocol and create a Windows VM and a Linux VM
- Install Wireshark from the Windows VM and start capturing packets
- Copy Linux VM private IP Address to ping from Windows VM using PowerShell
- Filter traffic for SSH and discover Linux information from PowerShell after pinging the Linux VM

<h2>Actions and Observations</h2>

<p>
<img width="965" height="505" alt="image" src="https://github.com/user-attachments/assets/2677a41a-ec5b-44da-bd35-480d139cedf8" />
</p>
<p>
I logged into both the Windows 11 VM and the Linux (Ubuntu) VM to analyze network communication between the two systems. From the Windows 11 VM, I installed Wireshark, a leading network protocol analyzer, by downloading it from wireshark.org. Using Wireshark, I initiated a packet capture on the active Ethernet interface by selecting it and clicking the shark fin icon to begin monitoring network activity traffic between both virtual machines. To verify the connectivity, I applied an ICMP filter to only view ICMP traffic, successfully confirming network communication between the Windows 11 and Ubuntu virtual machines.<br />

<p>
<img width="1177" height="615" alt="image" src="https://github.com/user-attachments/assets/b5680813-e502-4c50-b55e-013b47962f91" />
</p>
<p>
Next, I retrieved the Linux (Ubuntu) VM’s private IP address and opened PowerShell on the Windows 11 VM to perform a ping test to the Linux VM. I used Wireshark to monitor the packet exchange and analyze the network communication between the two systems. Within the captured data, the "Source" and "Destination" fields represented Layer 2 of the OSI Model (Data Link Layer), displaying the MAC addresses of the communicating devices. By expanding the Internet Protocol (IP) section, I identified Layer 3 of the OSI Model (Network Layer), which defines the logical addressing and routing of packets across the network.<br />

<p>
<img width="1182" height="596" alt="image" src="https://github.com/user-attachments/assets/06ea63db-6bf1-49b1-9016-a733fbf42af2" />
</p>
<p>
To establish a secure connection between the two virtual machines, I initiated an SSH (Secure Shell) session from the Windows 11 VM to the Linux (Ubuntu) VM. Using Wireshark, I applied an SSH traffic filter to see the encrypted communication. From PowerShell on the Windows 11 VM, I executed the command ssh <username>@<Linux_VM_Private_IP> to initiate the secure connection. Once connected, I ran commands such as "hostname," "id," and other general Linux commands to verify the remote access.<br />
