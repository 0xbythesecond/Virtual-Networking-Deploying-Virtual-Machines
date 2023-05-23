
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

Task 1: Create a virtual network with one subnet.
Task 2: Create two application security groups.
Task 3: Create a network security group and associate it with the virtual network subnet.
Task 4: Create inbound network security group rules to allow traffic to web servers and RDP to management servers.

Task 1: Create a virtual network

Sign in to the Azure portal using an account that has the Owner or Contributor role in the Azure subscription.
In the Azure portal, search for "Virtual networks" and select it from the results.
Click on "+ Create" on the Virtual networks blade.
On the Basics tab of the Create virtual network blade, provide the following details:
Subscription: Select the Azure subscription you are using for this lab.
Resource group: Click on "Create new" and enter the name "AZ500LAB07".
Name: Enter "myVirtualNetwork".
Region: Select "South Central US".
Switch to the IP addresses tab, set the IPv4 address space to "10.0.0.0/16", and set the Subnet address range to "10.0.0.0/24".
Click on "Review + create" and then click "Create" to create the virtual network.
Task 2: Create application security groups

In the Azure portal, search for "Application security groups" and select it from the results.
Click on "+ Create" on the Application security groups blade.
On the Basics tab of the Create an application security group blade, provide the following details:
Resource group: Select "AZ500LAB07".
Name: Enter "myAsgWebServers" (this group will be for web servers).
Click on "Review + create" and then click "Create".
Repeat steps 2-4 to create another application security group with the following details:
Resource group: Select "AZ500LAB07".
Name: Enter "myAsgMgmtServers" (this group will be for management servers).
Task 3: Create a network security group and associate it with the subnet

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
Task 4: Create inbound NSG security rules

On the myNsg blade, in the Settings section, click "Inbound security rules".
Review the default inbound security rules and then click "+ Add" to add a new rule.
On the Add inbound security rule.
