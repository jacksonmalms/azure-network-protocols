<p align="center">
<img src="https://i.imgur.com/u6eg9w4.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we will observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.


<h1>Important note:</h1>
This lab assumes you have already completed the previous lab/tutorial as it is the continuation of the last lab, if you have not already completed that one, go ahead and complete it and come back to this once you finish it. The link is listed below.

- [How to Setup VMs and a Virtual Network in Azure](https://github.com/jacksonmalms/create-azure-vm)<br />
<h1>Environments and Technologies Used</h1>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Overview</h2>

- Step 1: Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Step 2: Within your Windows 10 Virtual Machine, Install Wireshark
- Step 3: Ping the Ubuntu VM to observe ICMP traffic, disable and re-enable ICMP traffic through the NSG
- Step 4: Observe SSH traffic by connecting through the command line on the Windows VM
- Step 5: Observe DNS traffic on the Windows VM
- Step 6: Observe RDP traffic on the Windows VM
- Step 7: Clean up by deleting the resource groups to ensure we don't incur any charges or waste credits

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/UyHslgF.jpg"/>
</p>
<p>
First go to your Azure portal if it is not already open https://portal.azure.com/. 

Then get the public IP of the Windows VM and copy it, you can find that on the Virtual Machines section on the portal and clicking on the VM in question. Next, go to the Windows start menu and search "rdp" and open the RDP app, then paste the IP of the Windows VM in the first box and hit connect. Then enter the username and password that we set when we created the VM. Click OK.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
