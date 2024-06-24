# Azure Networking Resources Guide 🛰️

## Table of Contents 📋
1. [Introduction to Azure Virtual Networks](#introduction-to-azure-virtual-networks)
2. [Creating a Virtual Network](#creating-a-virtual-network)
3. [Subnets](#subnets)
4. [Network Security Groups (NSGs)](#network-security-groups-nsgs)
5. [Virtual Network Peering](#virtual-network-peering)
6. [VPN Gateway](#vpn-gateway)
7. [Azure DNS](#azure-dns)
8. [Load Balancer](#load-balancer)
9. [Additional Resources](#additional-resources)

## Introduction to Azure Virtual Networks 🌐

Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks.

## Creating a Virtual Network 💻

1. **Navigate to the Azure Portal**:
   - Go to [portal.azure.com](https://portal.azure.com/) and sign in with your Azure account.

2. **Create a Virtual Network**:
   - In the Azure portal, click on "Create a resource" in the left-hand menu.
   - Search for "Virtual Network" and select it.
   - Click "Create".

3. **Configure the Virtual Network**:
   - **Basics**: Select your subscription, resource group, and give your VNet a name (e.g., MyVNet). Choose a region.
   - **IP Addresses**: Define the address space (e.g., 10.0.0.0/16) and add subnets (e.g., 10.0.1.0/24).
   - **Security**: Default settings are fine for now.
   - **Review + create**: Click "Review + create" and then "Create".

## Subnets 📱

Subnets enable you to segment the virtual network into one or more subnetworks and allocate a portion of the virtual network's address space to each subnet. This helps you organize and secure your resources.

- **Create Subnets**: 
  - In the VNet configuration, add subnets with specific IP ranges.
  - Example: For a VNet with address space 10.0.0.0/16, you can create subnets like 10.0.1.0/24, 10.0.2.0/24, etc.

## Network Security Groups (NSGs) 🗃️

NSGs are used to filter network traffic to and from Azure resources in an Azure Virtual Network.

1. **Create an NSG**:
   - Navigate to "Network Security Groups" in the Azure portal.
   - Click "Create", provide necessary details, and assign it to your VNet/subnet or VM.

2. **Configure NSG Rules**:
   - Inbound and outbound rules can be set to allow or deny traffic based on source and destination IP, port, and protocol.

## Virtual Network Peering 🔧 

VNet peering connects two Azure VNets, enabling resources in each VNet to communicate with each other.

1. **Create Peering**:
   - Navigate to your VNet.
   - Select "Peerings" and then "Add".
   - Provide necessary details and choose the VNet you want to peer with.

2. **Configure Peering**:
   - Set options like allowing virtual network access, forwarding traffic, and gateway transit.

## VPN Gateway ⛩️

A VPN Gateway is a specific type of virtual network gateway that sends encrypted traffic between your virtual network and your on-premises location over the public Internet.

1. **Create a VPN Gateway**:
   - Navigate to "Create a resource" > "Networking" > "VPN Gateway".
   - Provide configuration details such as gateway type, VPN type, and virtual network.

## Azure DNS 📟

Azure DNS is a hosting service for DNS domains, providing name resolution using Microsoft Azure infrastructure.

1. **Create a DNS Zone**:
   - Navigate to "Create a resource" > "Networking" > "DNS zone".
   - Provide a name for your DNS zone and select a resource group.

2. **Manage DNS Records**:
   - Add, update, and delete DNS records within the DNS zone.

## Load Balancer ⚖️

Azure Load Balancer distributes incoming network traffic across multiple targets, such as VMs, within a region.

1. **Create a Load Balancer**:
   - Navigate to "Create a resource" > "Networking" > "Load Balancer".
   - Provide configuration details such as SKU, type, and virtual network.

2. **Configure Backend Pools and Rules**:
   - Define backend pools to distribute traffic and set load balancing rules.

## Additional Resources

- [Azure Virtual Network Overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [Azure Networking Documentation](https://learn.microsoft.com/en-us/azure/networking/)
- [Quickstart: Create a Virtual Network](https://learn.microsoft.com/en-us/azure/virtual-network/quick-create-portal)
- [Virtual Network Peering](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)
- [Network Security Groups](https://learn.microsoft.com/en-us/azure/virtual-network/security-overview)
- [Azure Load Balancer](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)
