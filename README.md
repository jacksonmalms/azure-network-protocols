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
<img src="https://i.imgur.com/iqT04F6.png"/>
</p>
<p>
When the VM loads up, uncheck all privacy settings. (It doesn't really matter, but it may be faster to set up this way)
</p>
<br />

<p>
<img src="https://i.imgur.com/a9O4aHG.png"/>
</p>
<p>
In the VM, open up edge and go to this URL https://www.wireshark.org/download.html (just copy/paste). Next download the Wireshark x64 installer.
</p>
<br />

<p>
<img src="https://i.imgur.com/9xIE2p1.jpg"/>
</p>
<p>
Now open the installer and install Wireshark with the defaults.
</p>
<br />

<p>
<img src="https://i.imgur.com/YEygB7e.png"/>
</p>
<p>
Once Wireshark opens, filter by "icmp" packets and hit the blue shark fin icon in the top left to start capturing traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/xa4Sj67.png"/>
</p>
<p>
Find your Ubuntu VM's private IP and copy it.
</p>
<br />

<p>
<img src="https://i.imgur.com/Ajzoggh.png"/>
</p>
<p>
Now go back to the VM open the command line and ping -t the private IP address of the Ubuntu VM to make continuous ICMP traffic that will be captured by Wireshark. We should see requests from the the Ubuntu VM's private IP, and replies from our Windows private IP as well.
</p>
<br />

<p>
<img src="https://i.imgur.com/FVyFq8w.png"/>
</p>
<p>
Now we are going to disable ICMP traffic from the Ubuntu VM's NSG (network security group) in the Azure portal. To do this, type "NSG" in the Azure portal searchbar and click into Network security groups.
</p>
<br />

<p>
<img src="https://i.imgur.com/T0yT1Ni.png"/>
</p>
<p>
Find the NSG for the Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/iAfxZZo.png"/>
</p>
<p>
Once you found the NSG for the Ubuntu VM, click on inbound security rules.
</p>
<br />

<p>
<img src="https://i.imgur.com/Ut5fruj.png"/>
</p>
<p>
Add a new rule with ICMP as the selected protocol, set the action to deny, and set the priority to any number that is lower than the first rule in the list (the lower the number, the higher the priority that the rule has) I set it to 299 as it has higher priority than 300. Now add the rule and wait for it to apply.
</p>
<br />

<p>
<img src="https://i.imgur.com/U6QJ1li.png"/>
</p>
<p>
Now going back into the VM, in the command line hit Ctrl + C to stop the continuous ping that we did with the ping -t command. Now hit the refresh button in Wireshark and continue without saving. Now try to ping the private IP of the Ubuntu VM again, now notice that our ping requests are now being timed out as we are not getting replies from our Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/Z91rAc3.png"/>
</p>
<p>
Now lets delete the NSG rule we made on the ubuntu VM
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />

<p>
<img src="https://i.imgur.com/m2pstmT.png"/>
</p>
<p>
Now try and to ping the Ubuntu VM again using the ping command. We now should see that the Ubuntu VM is now sending replies again!
</p>
<br />
