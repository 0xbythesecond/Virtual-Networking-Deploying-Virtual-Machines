
# Creating Virtual Networking Infrastructure and Deploying Virtual Machines


## Introduction
The lab consists of several tasks that will guide you through the process of creating a virtual network, setting up subnets, creating application security groups, configuring network security groups, and creating inbound security rules. These steps are essential for building a secure and well-structured virtual networking environment.

## Objective
By completing this lab, you will gain hands-on experience in creating and managing virtual networks in Azure, as well as understanding how to control network traffic using security groups and rules. This knowledge will be valuable for designing and implementing networking solutions in Azure, ensuring the security and efficiency of your virtual infrastructure.

Now, let's dive into the lab and start building your virtual networking infrastructure in Azure!

## Task to Implement Virtual Networking Infrastructure

Exercise 1: Create the virtual networking infrastructure

Estimated Time: 20 minutes

In this lab exercise, you will set up the virtual networking infrastructure by completing the following tasks:

Task 1: Create a virtual network with one subnet.<br/>
Task 2: Create two application security groups.<br/>
Task 3: Create a network security group and associate it with the virtual network subnet.<br/>
Task 4: Create inbound network security group rules to allow traffic to web servers and RDP to management servers.<br/>

<details> 
  <summary> Task 1: Create a virtual network </summary>

Sign in to the Azure portal using an account that has the Owner or Contributor role in the Azure subscription.<br />
- In the Azure portal, search for `Virtual networks` and select it from the results. <br />
- Click on `+ Create` on the Virtual networks blade.<br />
- On the Basics tab of the Create virtual network blade, provide the following details: <br />
- Subscription: Select the Azure subscription you are using for this lab.<br />
- Resource group: Click on `Create new` and enter the name `AZ500LAB07`.<br />
- Name: Enter `myVirtualNetwork`. <br />
- Region: Select `South Central US` or a region that would be nearest to you. 
  
<br />
<br />

|Setting	| Value|
| --------| --------|  
|Subscription |	the name of the Azure subscription you are using in this lab|
|Resource group	| click Create new and type the name AZ500LAB07|
|Name |	myVirtualNetwork |
|Region |	South Central US or Preferred Regions That is Nearest to You|
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Setting%20Up%20Virtual%20Network.png?raw=true" height="57%" width="59.3%" alt="Basics of Virtual Network"/>

Switch to the IP addresses tab, set the IPv4 address space to `10.0.0.0/16`, and set the Subnet address range to `10.0.0.0/24`
Click on `Review + create` and then click `Create` to create the virtual network.
  
| Setting |	Value |
| -------------  | ---------- |  
|Subnet name |	default |
|Subnet address range	| 10.0.0.0/24 |
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Review%20Creation%20of%20Virtual%20Network.png?raw=true" height="50%" width="50%" alt="Review Creation of Virtual Network"/>

  </details>
<hr>
  
  <details>
  <summary> Task 2: Create application security groups </summary>

In the Azure portal, search for `Application security groups` and select it from the results.
Click on `+ Create` on the Application security groups blade.
On the Basics tab of the Create an application security group blade, provide the following details:
Resource group: Select `AZ500LAB07` or your preferred Resource Group Name that would be that lab.
Name: Enter `myAsgWebServers` (this group will be for web servers).
Click on `Review + create` and then click `Create`.
Repeat steps 2-4 to create another application security group with the following details:
Resource group: Select `AZ500LAB07`.
Name: Enter `myAsgMgmtServers` (this group will be for management servers).
  
| Setting |	Value|
|----------- | ----------- |  
|Resource group |	AZ500LAB07|
|Name |	myAsgWebServers | 
| Region |	East US|
  
</details>
<hr>
<details> 
  <summary> Task 3: Create a network security group and associate it with the subnet</summary>

In the Azure portal, search for "Network security groups" and select it from the results.
Click on "+ Create" on the Network security groups blade.
On the Basics tab of the Create network security group blade, provide the following details:
Subscription: Select the Azure subscription you are using for this lab.
Resource group: Select "AZ500LAB07".
Name: Enter "myNsg".
Region: Select "East US".
Click on "Review + create" and then click "Create".
Navigate back to the Network security groups blade and select the "myNsg" entry.
On the myNsg blade, in the Settings section, click "Subnets" and then click "+ Associate".
On the Associate subnet blade, provide the following details:
Virtual network: Select "myVirtualNetwork".
Subnet: Select "default".
Click "OK" to associate the network security group with the subnet.
  </details>

<details>
  <summary> Task 4: Create inbound NSG security rules </summary>

- On the myNsg blade, in the Settings section, click "Inbound security rules". <br />
- Review the default inbound security rules and then click "+ Add" to add a new rule. <br />
- On the Add inbound security rule. <br />
- On the Add inbound security rule blade, specify the following settings to allow TCP ports 80 and 443 to the myAsgWebServers application security group (leave all other values with their default values):

| Setting |	Value |
|---------| --------|
|Destination |	in the drop-down list, select Application security group and then click myAsgWebServers|
|Destination| port ranges	80,443|
|Protocol |	TCP |
| Priority |	100 |
|Name |	Allow-Web-All|
  
  Lab Documentation: Creating Virtual Networking Infrastructure and Deploying Virtual Machines

Lab Overview:
The purpose of this lab is to guide you through the process of creating a virtual networking infrastructure in Azure and deploying virtual machines within that network. You will learn how to set up a virtual network, configure network security groups, create application security groups, and define inbound security rules to control network traffic. Additionally, you will deploy virtual machines and test network filters to validate the configuration.

Lab Steps:

Exercise 1: Create Virtual Network and Network Security

Add inbound security rule:
Navigate to the "myNsg" blade.
In the Settings section, click "Inbound security rules" and then click "+ Add."
On the "Add inbound security rule" blade, provide the following settings:
Destination: Select "Application security group" and choose "myAsgMgmtServers."
Destination port ranges: Enter "3389."
Protocol: Select "TCP."
Priority: Set it to "110."
Name: Enter "Allow-RDP-All."
Click "Add" to create the new inbound rule.
Result: You have added an inbound security rule to allow RDP (TCP port 3389) traffic to the "myAsgMgmtServers" application security group.

Exercise 2: Deploy Virtual Machines and Test Network Filters

Estimated timing: 25 minutes

Task 1: Create a Web Server Virtual Machine

Navigate to the Azure portal and search for "Virtual machines."
Click "+ Create" and select "+ Azure virtual machine" from the dropdown list.
On the Basics tab of the "Create a virtual machine" blade, provide the following settings:
Subscription: Select the Azure subscription for this lab.
Resource group: Choose "AZ500LAB07."
Virtual machine name: Enter "myVmWeb."
Region: Select "(US)East US."
Image: Choose "Windows Server 2022 Datacenter: Azure Edition - x64 Gen2."
Size: Select "Standard D2s v3."
Username: Enter "Student."
Password: Use your personal password created in Lab 04.
Confirm password: Retype your password.
Public inbound ports: Set it to "None."
Would you like to use an existing Windows Server License: Select "No."
Click "Next: Disks" and set the OS disk type to "Standard HDD."
Click "Next: Networking" and select the previously created network "myVirtualNetwork."
Under "NIC network security group," choose "None."
Click "Next: Management" and then "Next: Monitoring."
On the "Monitoring" tab, verify that "Boot diagnostics" is enabled with a managed storage account.
Click "Review + create" and ensure successful validation.
Click "Create" to deploy the virtual machine.
Task 2: Create a Management Server Virtual Machine

Navigate to the Azure portal and go to the Virtual machines blade.
Click "+ Create" and select "+ Azure virtual machine" from the dropdown list.
On the Basics tab of the "Create a virtual machine" blade, provide the following settings:
Subscription: Select the Azure subscription for this lab.
Resource group: Choose "AZ500LAB07."
Virtual machine name: Enter "myVMMgmt."
Region: Select "(US)East US."
Image: Choose "Windows Server 2022 Datacenter: Azure Edition - x64 Gen2."
Size: Select "Standard D2s v3."
Username: Enter "Student."
Password: Use your personal password created in Lab 04.
Public inbound ports: Set it to "None."
Already have a Windows Server license: Select "No."
Click "Next: Disks" and set the OS disk type to "Standard HDD."
Click "Next: Networking" and select the previously created network "myVirtualNetwork."
Under "NIC network security group," choose "None."
Click "Next: Management" and then "Next: Monitoring."
On the "Monitoring" tab, verify that "Boot diagnostics" is enabled with a managed storage account.
Click "Review + create" and ensure successful validation.
Click "Create" to deploy the virtual machine.
Note: Wait for both virtual machines to be provisioned before continuing.

Task 3: Associate Network Interfaces with Application Security Groups

Go to the Virtual machines blade in the Azure portal and verify that both virtual machines are listed with the "Running" status.
Click the entry for the "myVMWeb" virtual machine.
On the "myVMWeb" blade, click "Networking" in the Settings section.
On the "myVMWeb | Networking" blade, click the "Application security groups" tab.
Click "Configure the application security groups" and select "myAsgWebServers" from the Application security group drop-down list.
Click "Save."
Navigate back to the Virtual machines blade and click the entry for the "myVMMgmt" virtual machine.
On the "myVMMgmt" blade, click "Networking" in the Settings section.
On the "myVMMgmt | Networking" blade, click the "Application security groups" tab.
Click "Configure the application security groups" and select "myAsgMgmtServers" from the Application security group drop-down list.
Click "Save."
Task 4: Test Network Traffic Filtering

Go to the "myVMMgmt" virtual machine blade in the Azure portal.
Click "Connect" and select "RDP" from the drop-down menu.
Download the RDP file and use it to connect to the "myVMMgmt" Azure VM via Remote Desktop using the provided credentials.
In the Azure portal, navigate to the "myVMWeb" virtual machine blade.
On the "myVMWeb" blade, in the Operations section, click "Run command" and then select "RunPowerShellScript."
Run the following command in the Run Command Script pane to install the Web server role on "myVMWeb":
arduino
Copy code
Install-WindowsFeature -name Web-Server -IncludeManagementTools
Wait for the installation to complete.
In the Azure portal, navigate back to the "myVMWeb" blade.
Identify the Public IP address of the "myVmWeb" Azure VM.
Open another browser tab and navigate to the identified IP address.
Verify that the default IIS web page is displayed, indicating that port 80 is allowed inbound from the internet based on the "myAsgWebServers" application security group.
Result: You have successfully validated the network security group (NSG) and application security group (ASG) configuration, and the network traffic is being correctly managed.

Lab Cleanup:
To avoid incurring unexpected costs, it is essential to remove any unused Azure resources.

Open the Cloud Shell by clicking the first icon in the top right of the Azure Portal.
If prompted, select PowerShell and Create storage.
In the PowerShell session within the Cloud Shell pane, run the following command to remove the




Regenerate response

Continue generating

  
  </details>
