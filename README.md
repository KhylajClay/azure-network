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
Log in to Windows 11 VM and Linux VM (Ubuntu). Install Wireshark from the Windows 11 VM. Google, https://www.wireshark.org, and install. This is the protocol analyzer and lets us observe the traffic between the two Virtual Machines. Now we will start a packet capture, highlight the "Ethernet", and click on the sharkfin. Now we can see all of the network traffic on the backend. Filter it for ICMP traffic to test the connectivity between the two Virtual Machines.   </p>
<br />

<p>
<img width="1177" height="615" alt="image" src="https://github.com/user-attachments/assets/b5680813-e502-4c50-b55e-013b47962f91" />
</p>
<p>
Get the Linux VM private IP Address, open up PowerShell from Windows 11 VM, and we will attempt to ping the Linux VM from the Windows VM and inspect it from Wireshark. The "Destination" and "Source" fall under Layer 2 of the OSI Model. It's the MAC Address of this computer. If you expand Internet Protocol, you will discover Layer 3 of the OSI Model, and it's the network layer. </p>
<br />

<p>
<img width="1182" height="596" alt="image" src="https://github.com/user-attachments/assets/06ea63db-6bf1-49b1-9016-a733fbf42af2" />
</p>
<p>
Now we will make a secure connection from one Virtual Machine to another. We will make an SSH from a Windows VM to a Linux VM. Go back to Wireshark and filter traffic for SSH. Open PowerShell from Windows, and type "(ssh) (username of vm@private IP address of Linux VM)" to ping for the SSH traffic. If you type host hostname, ID, and any general information, we should now be able to see Linux information even though we are on the Windows VM. </p>
<br />
