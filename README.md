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

- Step 1 Create a Windows 10 Virtual Machine (VM) with 2 Virtual CPUs and allow it to create a new Virtual Network (Vnet)
- Step 2 Create a Ubuntu Server Virtual Machine (VM) with 2 Virtual CPUs and have it use the Virtual Network from the Windows 10 Virtual Machine (VM) 
- Step 3 Remote into Windows 10 Virtual Machine, install wireshark, and observer various traffic while performing commands with Windows Powershell
- Step 4 Set a perpetual ping with Windows Powershell for the Ubuntu Server, then block icmp v4 with Microsoft Azure Network Security Group and observe traffic changes 

<h2>Actions and Observations</h2>

![image](https://github.com/user-attachments/assets/198a231c-66ca-49b5-a303-7fa525feaf8a)

<p>
Create VM1 Windows 10 in Microsoft Azure
</p>
<br />

![vm2](https://github.com/user-attachments/assets/2d32d0c3-21be-4ad8-a26d-68bc2e016fc0)

<p>
Create VM2 Ubuntu Server in Microsoft Azure
</p>
<br />

![ping1](https://github.com/user-attachments/assets/105b3899-00cc-4733-8727-1b42bfafb42d)


<p>
Use wireshark to monitor traffic.
</p>
<br />

![image](https://github.com/user-attachments/assets/ff6dadc6-2376-4ce5-ab4e-c91d66380c32)

<p>
Block inbound traffic for ICMP v4 and view traffic change with Powershell. 
</p>
<br />
