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
- Step 3 Remote into Windows 10 Virtual Machine, install Wireshark, and observe various traffic while performing commands with Windows Powershell
- Step 4 Set a perpetual ping with Windows Powershell for the Ubuntu Server, then block icmp v4 with Microsoft Azure Network Security Group and observe traffic changes 

<h2>Actions and Observations</h2>

![1](https://github.com/user-attachments/assets/440b44ba-85a4-4d30-9dd7-5dbb9d90a5b4)

Create a Virtual Machine and Resource group in Microsoft Azure
Type Virtual Machine in search bar->click Virtual Machine->click create and select Azure Virtual Machine

<br />
<br />


![image](https://github.com/user-attachments/assets/883aacc6-cb48-4e8c-9d74-02dc1e30695d)



![image](https://github.com/user-attachments/assets/198a231c-66ca-49b5-a303-7fa525feaf8a)

<p>
Click create new under Resource Group Name Rglab1-> Name Virtual Machine vm1-> Select  Windows 10 Pro, version 22h2-Gen 2 for image=> Select E2 v3 (2 vcpus, 16 GiB memory for size-> Set Administrator name and password-> Scroll to bottom and confirm licensing -> Click review and create-> Once validation has passed click create
</p>
<br />

![vm2](https://github.com/user-attachments/assets/2d32d0c3-21be-4ad8-a26d-68bc2e016fc0)

<p>
Ensure same region and zone are used-> Create VM2 Ubuntu Server in Microsoft Azure following the same steps as creating vm1-> Use same Resource Group-> Name vm2-> Select Ubuntu Server 24.04 LTS x64 Gen2 for image-> Select password under Authentication Type and use same name and password as VM1-> Scroll to bottom and click next twice-> In networking ensure vm1-vnet is selected for virtual network-> Click review and create->Once validation has passed click create 
</p>
<br />
<br />


![image](https://github.com/user-attachments/assets/c5f3df4e-ab14-4ee2-8df3-96279bd22783)

Click on your Virtual Machine (vm1) so that you can see the Public IP Address-> In Windows open Remote Desktop Connection-> Type in Public IP address and credentials and click connect

<br />
<br />

![4](https://github.com/user-attachments/assets/22c95e6f-571f-4375-be85-f8343a2f44fb)

Open up a web browser in vm1-> Go to url www.wiresharkorg/download.html-> Click and download Windows x64 Installer-> Install Wireshark with preselected settings-> Open application Wireshark

<br />
<br />

![5](https://github.com/user-attachments/assets/ebc41baf-4817-4886-a6b6-6214bdbc3b83)

Click first button below the files menu to start monitoring traffic


<br >
<br />

![ping1](https://github.com/user-attachments/assets/105b3899-00cc-4733-8727-1b42bfafb42d)


<p>
Open start menu and type Windows Power Shell-> Click run as Administrator-> Type ping wwww.google.com in Windows Power Shell
</p>
<br />
<br />

![10](https://github.com/user-attachments/assets/0aea474e-1954-4965-a641-a4063287eefa)

In Microsoft Azure click on vm2-> copy Private IP address

<br />
<br />


![11](https://github.com/user-attachments/assets/8ffd965a-f4ac-4754-82f7-ecff99b4004b)

In Virtual Machine (vm1) type icmp for the filter in Wireshark-> Set perpetual ping by typing ping the private IP Address -t in Windows Powershell

<br />
<br />

![6](https://github.com/user-attachments/assets/c683723a-5316-4dd3-91e8-84e90014a8d5)

![7](https://github.com/user-attachments/assets/f1ce03a7-5488-41d6-bbdc-ec9993a288b8)

![8](https://github.com/user-attachments/assets/35ad835a-6975-4cab-a573-59425b02a4e4)

In Microsoft Azure search Network Security Group and click on it-> Select VM2, Settings, Inbound Security Rules-> Click Add and set rule to Protocol (ICMPv4), priority 200, and click add

<br />
<br />



![image](https://github.com/user-attachments/assets/ff6dadc6-2376-4ce5-ab4e-c91d66380c32)

View perpetual ping time out in Virtual Machine (vm1) in Wireshark and Windows Power Shell

<br />
<br />

![13](https://github.com/user-attachments/assets/f7df538f-c1a6-4958-9ef2-9fcbc3c202c3)


Go back to Microsoft Azure Network Security Group and delete the rule by clicking the garbage can on the far right of the rule. 

<br />
<br />

![14](https://github.com/user-attachments/assets/4c4ca60d-8ae1-415f-abae-d03598152f74)


View perpetual ping resume in Wireshark and Windows Power Shell.

**Note to stop perpetual ping with Windows Power Shell selected click Control + C**
