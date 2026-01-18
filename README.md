# Microsoft Azure – VNet Peering Across Different Regions

## Overview
This project demonstrates **cross-region communication between Azure virtual machines** using **Virtual Network (VNet) Peering**.  
The lab highlights how Azure VNets deployed in **different geographic regions** can securely communicate with each other without using public IP addresses.

Initially, virtual machines deployed in separate regions were **unable to communicate**. After implementing **VNet Peering**, seamless private connectivity was achieved across regions.

This project reflects a **real-world global Azure networking scenario**.

---

## Technologies Used
- Microsoft Azure
- Azure Virtual Networks (VNet)
- Azure VNet Peering
- Azure Virtual Machines (Windows)
- Azure Resource Groups
- Azure Portal

---

## Architecture Overview
The architecture consists of:

- **East US Region**
  - Virtual Network (VNet-East)
  - Virtual Machine with Web Server installed

- **North Europe Region**
  - Virtual Network (VNet-NorthEU)
  - Virtual Machine used to test connectivity

- **VNet Peering**
  - Enabled between East US and North Europe VNets
  - Allows private IP communication across regions

**Traffic Flow:**

VM (North Europe)  
⬇  
Azure VNet Peering  
⬇  
Web Server VM (East US)

---

## Implementation Steps

### Step 1: Resource Group and Virtual Network Creation
A resource group named **Testing** was created to manage all Azure resources.  
Two virtual networks were deployed:
- One in **East US**
- One in **North Europe**

Each VNet used a **non-overlapping IP address range**.

---

### Step 2: Virtual Machine Deployment
Virtual machines were deployed in each region:
- **East US VM**
  - Hosted a web server service
- **North Europe VM**
  - Used to test cross-region connectivity

Initially, both VMs were isolated within their respective VNets.

---

### Step 3: Initial Connectivity Test (Failure)
The web server hosted on the **East US VM** was tested from the **North Europe VM**.  
The connection **failed**, confirming that:
- VNets in different regions do not communicate by default

---

### Step 4: Configuring VNet Peering
VNet Peering was configured between:
- East US VNet → North Europe VNet
- North Europe VNet → East US VNet

Peering settings allowed:
- Virtual network access
- Forwarded traffic

This established private, low-latency connectivity between regions.

---

### Step 5: Validation and Successful Connectivity
After peering was enabled:
- The website hosted on the East US VM became accessible from the North Europe VM
- Connectivity was established using **private IP addresses**
- No public IP communication was required

---

## Results
- Successful cross-region VM communication
- Secure private connectivity across Azure regions
- Improved network design using Azure best practices
- Demonstrated real-world global Azure networking

---

## Screenshots

### Azure Virtual Machine – East US
![Azure VNet Peering](screenshots/azure-vnet-peering-multiregion.png)

---

## Video Demonstration
▶️[Watch Azure VNet Peering Multi-Region Demo]()

## Key Learnings
- Azure VNet communication behaviour
- Importance of VNet Peering for multi-region deployments
- Designing global cloud networks
- Troubleshooting Azure connectivity issues
- Secure and scalable Azure networking

---

## Future Enhancements
- Implement Azure VPN Gateway or ExpressRoute
- Add Network Security Groups (NSGs) for granular control
- Enable Azure Monitor and Network Watcher
- Implement hub-and-spoke architecture
