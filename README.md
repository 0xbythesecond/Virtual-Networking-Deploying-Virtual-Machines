
# Creating Virtual Networking Infrastructure and Deploying Virtual Machines

![Network and Application Security Groups](https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Network%20and%20Application%20Security%20Group.png?raw=true)

## Introduction
The lab consists of several tasks that will guide you through the process of creating a virtual network, setting up subnets, creating application security groups, configuring network security groups, and creating inbound security rules. These steps are essential for building a secure and well-structured virtual networking environment.

## Objective
By completing this lab, you will gain hands-on experience in creating and managing virtual networks in Azure, as well as understanding how to control network traffic using security groups and rules. This knowledge will be valuable for designing and implementing networking solutions in Azure, ensuring the security and efficiency of your virtual infrastructure. This lab is from Microsoft's AZ-500 exam preparation walkthrough that can be found [here](https://microsoftlearning.github.io/AZ500-AzureSecurityTechnologies/Instructions/Labs/LAB_07_NSGs.html).

Now, let's dive into the lab and start building your virtual networking infrastructure in Azure!

## Task to Implement Virtual Networking Infrastructure

### *Exercise 1: Create the virtual networking infrastructure*

Estimated Time: 20 minutes

In this lab exercise, you will set up the virtual networking infrastructure by completing the following tasks:

Task 1: Create a virtual network with one subnet.<br/>
Task 2: Create two application security groups.<br/>
Task 3: Create a network security group and associate it with the virtual network subnet.<br/>
Task 4: Create inbound network security group rules to allow traffic to web servers and RDP to management servers.<br/>

<details> 
  <summary> Exercise 1 ---> Task 1: Create a virtual network </summary>

Sign in to the Azure portal using an account that has the Owner or Contributor role in the Azure subscription.
  <br />
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
  <summary> Exercise 1 ---> Task 2: Create application security groups </summary>

In the Azure portal, search for `Application security groups` and select it from the results.
  <br />
- Click on `+ Create` on the Application security groups blade.<br />
- On the Basics tab of the Create an application security group blade, provide the following details:<br />
- Resource group: Select `AZ500LAB07` or your preferred Resource Group Name that would be that lab.<br />
- Name: Enter `myAsgWebServers` (this group will be for web servers).<br />
- Click on `Review + create` and then click `Create`.
- Repeat steps 2-4 to create another application security group with the following details:<br />
- Resource group: Select `AZ500LAB07`.<br />
- Name: Enter `myAsgMgmtServers` (this group will be for management servers).<br />
  
| Setting |	Value|
|----------- | ----------- |  
|Resource group |	AZ500LAB07|
|Name |	myAsgWebServers | 
| Region |	South Central US|
  
  >**Note**: This group will be for the web servers.

<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Create%20ASG%20WebServers.png?raw=true" height="60%" width="60%" alt="websever asg"/>  
  
|Setting |	Value|
|----------- | ------------ |  
|Resource group |	AZ500LAB07|
|Name	| myAsgMgmtServers|
|Region |	South Central US|
  >**Note**: This group will be for the management servers.  
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Create%20ASG%20MgmtServers.png?raw=true" height="60%" width="60%" alt="mgmtserver asg"/>
  
</details>
<hr>
<details> 
  <summary> Exercise 1 ---> Task 3: Create a network security group and associate it with the subnet</summary>

In the Azure portal, search for `Network security groups` and select it from the results.
  <br />
- Click on `+ Create` on the Network security groups blade.<br />
- On the Basics tab of the Create network security group blade, provide the following details:<br />
- Subscription: Select the Azure subscription you are using for this lab.<br />
- Resource group: Select `AZ500LAB07`.<br />
- Name: Enter `myNsg`.<br />
- Region: Select `East US`.<br />
- Click on "Review + create" and then click `Create`.<br />
  
| Setting |	Value|
| ----------- | ----------- |  
|Subscription |	the name of the Azure subscription you are using in this lab|
|Resource group	| AZ500LAB07|
|Name	| myNsg|
| Region |	South Central US|
 
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Create%20NSG.png?raw=true" height="60%" width="60%" alt="Create NSG"/>  
  
- Navigate back to the Network security groups blade and select the `myNsg` entry.<br />
- On the myNsg blade, in the Settings section, click `Subnets` and then click `+ Associate`.<br />
- On the Associate subnet blade, provide the following details:<br />
- Virtual network: Select `myVirtualNetwork`.<br />
- Subnet: Select `default`.<br />
- Click `OK` to associate the network security group with the subnet.<br />
 
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Associate%20NSG%20Subnet.png?raw=true" height="90%" width="90%" alt="Associate Subnet"/>  
  
| Setting |	Value |
| ----------- | -------- |  
|Virtual network	| myVirtualNetwork|
| Subnet |	default|

  </details>
<hr>
<details>
  <summary> Exercise 1 ---> Task 4: Create inbound NSG security rules </summary>

- On the myNsg blade, in the Settings section, click `Inbound security rules`. <br />
- Review the default inbound security rules and then click `+ Add` to add a new rule. <br />
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Add%20Inbound%20Security%20Rules.png?raw=true" height="60%"  width="60%" alt="Select to Add an inbound security rule"/>
  
- On the Add inbound security rule. <br />
- On the Add inbound security rule blade, specify the following settings to allow TCP ports 80 and 443 to the myAsgWebServers application security group (leave all other values with their default values):

| Setting |	Value |
|---------| --------|
|Destination |	in the drop-down list, select Application security group and then click `myAsgWebServers`|
|Destination| port ranges	80,443|
|Protocol |	TCP |
| Priority |	100 (lower the number, the higher the priority) |
|Name |	Allow-Web-All|
 
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Enter%20Values%20for%20NSG%20Inbound%20Security%20Rules.png?raw=true" height="50%" width="60%" alt="Inbound Security Rule Settings myVMWeb"/>  
<br />
  
Add inbound security rule:
- Navigate to the "myNsg" blade. <br />
- In the Settings section, click "Inbound security rules" and then click "+ Add."<br />
- On the "Add inbound security rule" blade, provide the following settings:<br />
- Destination: Select "Application security group" and choose "myAsgMgmtServers."<br />
- Destination port ranges: Enter "3389."<br />
- Protocol: Select "TCP."<br />
- Priority: Set it to "110."<br />
- Name: Enter "Allow-RDP-All."<br />
- Click "Add" to create the new inbound rule.<br />
- Result: You have added an inbound security rule to allow RDP (TCP port 3389) traffic to the "myAsgMgmtServers" application security group.
 

|Setting	| Value|
|---------- | ----------- |  
| Destination |	in the drop-down list, select Application security group and then click `myAsgMgmtServers`|
|Destination port ranges |	3389|
|Protocol	| TCP |
| Priority |	110 |
| Name |	Allow-RDP-All|

<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Enter%20Values%20for%20NSG%20Inbound%20Security%20Rules%20(asg%20mgmt).png?raw=true" height="50%" width="60%" alt="Inbound Security Rules Settings myVMMgmt"/>
  
  >**Note**: Result: You have deployed a virtual network, network security with inbound security rules, and two application security groups.
  
</details>
<hr>
<br />

### *Exercise 2: Deploy Virtual Machines and Test Network Filters*

Estimated timing: 25 minutes

In this exercise, you will complete the following tasks:

Task 1: Create a virtual machine to use as a web server.<br />
Task 2: Create a virtual machine to use as a management server.<br />
Task 3: Associate each virtual machines network interface to it’s application security group.<br />
Task 4: Test the network traffic filtering.<br />

<details> 
  <summary> Exercise 2 ---> Task 1: Create a virtual machine to use as a web server.</summary>
<br />
Navigate to the Azure portal and search for `Virtual machines.`
- Click `+ Create` and select `+ Azure virtual machine` from the dropdown list.
  <br />
  
  <img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Create%20Virtual%20Machine.png?raw=true" height="30%" width="30%" alt="Create Virtual Machine Initial Step"/>
  
- On the Basics tab of the "Create a virtual machine" blade, provide the following settings:<br />
- Subscription: Select the Azure subscription for this lab.<br />
- Resource group: Choose `AZ500LAB07`<br />
- Virtual machine name: Enter `myVmWeb`<br />
- Region: Select `(US)South Central US or the nearest region to you`<br />
- Image: Choose `Windows Server 2022 Datacenter: Azure Edition - x64 Gen2`<br />
- Size: Select `Standard D2s v3`<br />
- Username: Enter `Student`<br />
- Password: Use your personal password.<br />
- Confirm password: Retype your password.<br />
- Public inbound ports: Set it to 'None'<br />
- Would you like to use an existing Windows Server License: 'Leave selection unchecked`<br />
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/create%20virtual%20machine%20(values).png?raw=true" height="70%" width="70%" alt="Virtual Machine Settings for Server"/>   



- Click "Next: Disks" and set the OS disk type to `Standard HDD`<br />
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Select%20OS%20Disk%20Type.png?raw=true" height="50%" width="50%" alt="Select Os Disk Type"/>
  
- Click "Next: Networking" and select the previously created network `myVirtualNetwork`<br />
- Under "NIC network security group," choose `None`<br />
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Values%20for%20Networking%20on%20VM.png?raw=true" height="50%" width="50%" alt="Networking Settings for myVMWeb"/>
  
- Click "Next: Management" and then "Next: Monitoring."<br />
- On the "Monitoring" tab, verify that "Boot diagnostics" is enabled with a managed storage account.<br />
  
| Setting |	Value|
|------------------ | ---------------- |  
| Boot diagnostics |	Enabled with managed storage account (recommended) |
  
- Click "Review + create" and ensure successful validation.<br />
- Click "Create" to deploy the virtual machine.<br />

|Setting |	Value |
| ------------ | ----------- |  
|Subscription |	the name of the Azure subscription you will be using in this lab |
|Resource group |	AZ500LAB07|
|Virtual machine name	| myVmWeb |
|Region	|(US) South Central US|
|Image |	Windows Server 2022 Datacenter: Azure Edition- x64 Gen2|
|Size |	Standard D2s v3 |
|Username |	Student|
|Password |	Please use your personal password created|
|Confirm password |	Retype your password|
|Public inbound ports |	None|
|Would you like to use an existing Windows Server License |	No  |
  
</details>
<hr>
<details> 
  <summary> Exercise 2 ---> Task 2: Create a Management Server Virtual Machine</summary>
<br />
Navigate to the Azure portal and go to the Virtual machines blade.<br />
  
  >**Note**: The following will be the same as the previous Virtual Machine except for the Management Server, so no pictured image. 
  
- Click `+ Create` and select `+ Azure virtual machine` from the dropdown list.<br />
- On the Basics tab of the "Create a virtual machine" blade, provide the following settings:<br />
- Subscription: Select the Azure subscription for this lab.<br />
- Resource group: Choose `AZ500LAB07.`<br />
- Virtual machine name: Enter `myVMMgmt.`<br />
- Region: Select `South Central US`<br />
- Image: Choose `Windows Server 2022 Datacenter: Azure Edition - x64 Gen2.`<br />
- Size: Select `Standard D2s v3.`<br />
- Username: Enter `Student.`<br />
- Password: Use your personal password.<br />
- Public inbound ports: Set it to `None.`<br />
- Already have a Windows Server license: Select `No.`<br />
  
| Setting |	Value |
| ---------- | ----------- |  
| Subscription |	the name of the Azure subscription you will be using in this lab |
| Resource group |	AZ500LAB07|
| Virtual machine name |	myVMMgmt |
| Region |	South Central US or preferred region that is nearest to you|
| Image	| Windows Server 2022 Datacenter: Azure Edition - x64 Gen2 |
| Size |	Standard D2s v3|
| Username |	Student|
| Password |	Please use your personal password that you create|
| Public inbound ports |	None|
| Already have a Windows Server license |	No|
  
  >**Note**: For public inbound ports, we will rely on the precreated NSG.

- Click `Next: Disks` and set the OS disk type to `Standard HDD`<br />
- Click `Next: Networking` and select the previously created network `myVirtualNetwork`<br />
- Under "NIC network security group," choose `None.`<br />
- Click "Next: Management" and then `Next: Monitoring.`<br />
- On the "Monitoring" tab, verify that `Boot diagnostics` is enabled with a managed storage account.<br />
- Click `Review + create` and ensure successful validation.<br />
- Click `Create` to deploy the virtual machine.
  
  >**Note**: Wait for both virtual machines to be provisioned before continuing.
  
  </details>
<hr>

<details>
  <summary> Exercise 2 ---> Task 3: Associate Network Interfaces with Application Security Groups</summary> 
<br />
Go to the Virtual machines blade in the Azure portal and verify that both virtual machines are listed with the "Running" status.<br />
  
- Click the entry for the "myVMWeb" virtual machine.<br />
- On the "myVMWeb" blade, click "Networking" in the Settings section.<br />
- On the "myVMWeb | Networking" blade, click the "Application security groups" tab.<br />
- Click "Configure the application security groups" and select "myAsgWebServers" from the Application security group drop-down list.<br />

  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Configure%20Application%20Security%20Groups%20for%20NiC%20(myVmWeb).png?raw=true" height="80%" width="80%" alt="Associate NiC with ASG on myVWeb"/>

 <br /> 
 - Click "Save."<br /> 
 <img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Configure%20Application%20Security%20Groups%20for%20NiC%20(myVmWeb%202).png?raw=true" height="50%" width="50%" alt="Save myASGWebServers for Association"/>
  
  >**Note**: The following steps and settings are the same as previously mentioned with the exception of the change for `myVMMgmt` and `myAsgMgmtServers`
  
- Navigate back to the Virtual machines blade and click the entry for the "myVMMgmt" virtual machine.<br />
- On the "myVMMgmt" blade, click "Networking" in the Settings section.<br />
- On the "myVMMgmt | Networking" blade, click the "Application security groups" tab.<br />
- Click "Configure the application security groups" and select "myAsgMgmtServers" from the Application security group drop-down list.<br />
- Click "Save."
  </details>
  <hr>
  
<details>
  <summary> Exercise 2 ---> Task 4: Test Network Traffic Filtering and Lab Clean Up</summary>
<br />
Go to the "myVMMgmt" virtual machine blade in the Azure portal.<br />
  
- Click "Connect" and select "RDP" from the drop-down menu.<br />
- Download the RDP file and use it to connect to the "myVMMgmt" Azure VM via Remote Desktop using the provided credentials.<br />
- In the Azure portal, navigate to the "myVMWeb" virtual machine blade.<br />
- On the "myVMWeb" blade, in the Operations section, click "Run command" and then select "RunPowerShellScript."<br />
 
 <img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Run%20PowerShell%20Command.png?raw=true" height="90%" width="90%" alt="Select Run Command to Execute PowerShell Script"/>  
  
- Run the following command in the Run Command Script pane to install the Web server role on "myVMWeb":
  
```powershell
Install-WindowsFeature -name Web-Server -IncludeManagementTools
```  
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Run%20Powershell%20Script.png?raw=true" height="60%" width="60%" alt="Run Powershell Script to Install Web Server Rolse myVMWeb"/>
  
  >**Note**: Wait for the installation to complete. There will be a notification of success. 
  
- In the Azure portal, navigate back to the "myVMWeb" blade. <br />
- Identify the Public IP address of the "myVmWeb" Azure VM.<br />
 
  <img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Identify%20Public%20IP%20Address.png?raw=true" height="100%" width="100%" alt="identify public IP address"/> 
  
- Open another browser tab and navigate to the identified IP address.<br />
- Verify that the default IIS web page is displayed, indicating that port 80 is allowed inbound from the internet based on the "myAsgWebServers" application security group.<br />
  
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/IIS%20Webpage%20Validation.png?raw=true" height="60%" width="60%" alt="IIS Webpage Validation"/>  
  
  >**Note**:Result: You have successfully validated the network security group (NSG) and application security group (ASG) configuration, and the network traffic is being correctly managed.

Lab Cleanup:
To avoid incurring unexpected costs, it is essential to remove any unused Azure resources.

Open the Cloud Shell by clicking the first icon in the top right of the Azure Portal.<br />
If prompted, select PowerShell and Create storage.<br />
In the PowerShell session within the Cloud Shell pane, run the following command to remove the resource group you created in this lab:<br />

```powershell
 Remove-AzResourceGroup -Name "AZ500LAB07" -Force -AsJob
```
<img src="https://github.com/0xbythesecond/Virtual-Networking-Deploying-Virtual-Machines/blob/main/Run%20Powershell%20Resource%20Group%20Delete%20Script.png?raw=true" height="80%" width="80%" alt="Powershell Command to Delete Resource Group"/>
  
Close the Cloud Shell pane.

  >**Note**:  Remember to remove any newly created Azure resources that you no longer use. Removing unused resources ensures you will not incur unexpected costs.
  
  </details>
  
 ## Reflection
Through the process of creating a virtual network, application security groups, and network security groups, I gained hands-on experience in configuring and securing network resources in Azure. This exercise allowed me to understand the importance of properly defining IP addresses, subnets, security rules, and associations between resources.

I learned how to navigate the Azure portal and utilize various settings and options to create and configure virtual machines, assign security groups, and manage network traffic. The step-by-step instructions provided clear guidance, enabling me to follow along and successfully complete the tasks.

By associating network interfaces with application security groups, I experienced firsthand how traffic filtering can be implemented and managed at a granular level. This approach enhances security by allowing only authorized traffic to reach specific resources, such as web servers and management servers.

Overall, this exercise helped me develop practical skills in network resource management and security within the Azure environment. I feel more confident in my ability to create and configure virtual networks and apply appropriate security measures to protect my applications and data.

## Conclusion
Creating a VNet (virtual network) and implementing network and application security groups are crucial steps in ensuring the secure and efficient operation of cloud-based resources. Azure provides a booming set of tools and features that streamline the configuration and management of network resources.

Through careful configuration of IP addresses, subnets, and security rules, an organization(s) can create distinct network environments that offer isolation, precise control over traffic, and effective mitigation of potential security vulnerabilities. Application security groups enable fine-grained access control, allowing specific groups of resources to communicate with each other while restricting unauthorized access.

The ability to associate network interfaces with application security groups further enhances security and simplifies management. By grouping resources based on their intended roles or functions, administrators can apply consistent security policies and streamline the management of network traffic.

Through this exercise, I have gained valuable hands-on experience in creating virtual networks, configuring security groups, and managing network traffic in Azure. These skills will prove invaluable in designing and implementing secure and scalable cloud-based architectures.

As I continue to explore Azure and its networking capabilities, I will further refine my understanding of network security best practices and continue to strengthen my ability to design and implement robust and secure network architectures in the cloud.
