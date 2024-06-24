# Azure Virtual Networks and Hub-and-Spoke Architecture Guide 🕸️

## Table of Contents 📋
1. [Create a Virtual Network with Subnets](#create-a-virtual-network-with-subnets)
   - Subnet-1: Linux VM, Windows VM
   - Subnet-2: SQL DB
2. [Create 4 VNets](#create-4-vnets)
   - Management VNet (HUB)
   - Production VNet
   - Testing VNet
   - Developing VNet
3. [Configure Hub-and-Spoke Architecture](#configure-hub-and-spoke-architecture)
4. [Verify Connectivity](#verify-connectivity)
5. [Additional Resources](#additional-resources)

## Create a Virtual Network with Subnets 🛜

### Step 1: Create a Virtual Network
1. **Navigate to the Azure Portal**:
   - Go to [portal.azure.com](https://portal.azure.com/) and sign in with your Azure account.

2. **Create a Virtual Network**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "Virtual Network" and select it.
   - Click "Create".

3. **Configure the Virtual Network**:
   - **Basics**: Select your subscription, resource group, and give your VNet a name (e.g., `MainVNet`). Choose a region.
   - **IP Addresses**: Define the address space (e.g., `10.0.0.0/16`).

### Step 2: Create Subnets
1. **Create Subnet-1**:
   - Name: `Subnet-1`
   - Address range: `10.0.1.0/24`

2. **Create Subnet-2**:
   - Name: `Subnet-2`
   - Address range: `10.0.2.0/24`

3. **Review + create**: Click "Review + create" and then "Create".

### Step 3: Create Virtual Machines
1. **Create a Linux VM in Subnet-1**:
   - Navigate to "Create a resource" > "Compute" > "Virtual Machine".
   - Configure the VM, ensuring it is placed in `Subnet-1` of `MainVNet`.
   
2. **Create a Windows VM in Subnet-1**:
   - Follow the same steps as for the Linux VM, but choose a Windows image.

3. **Create a SQL Database in Subnet-2**:
   - Navigate to "Create a resource" > "Databases" > "SQL Database".
   - Configure the database, ensuring it is placed in `Subnet-2` of `MainVNet`.

## Create 4 VNets 🔗

### Step 1: Create the Management VNet (HUB)
1. **Create Management VNet**:
   - Follow the steps to create a VNet.
   - Name: `ManagementVNet`
   - Address space: `10.1.0.0/16`
   - Subnet: `ManagementSubnet` with address range `10.1.1.0/24`

### Step 2: Create the Production VNet
1. **Create Production VNet**:
   - Follow the steps to create a VNet.
   - Name: `ProductionVNet`
   - Address space: `10.2.0.0/16`
   - Subnet: `ProductionSubnet` with address range `10.2.1.0/24`

### Step 3: Create the Testing VNet
1. **Create Testing VNet**:
   - Follow the steps to create a VNet.
   - Name: `TestingVNet`
   - Address space: `10.3.0.0/16`
   - Subnet: `TestingSubnet` with address range `10.3.1.0/24`

### Step 4: Create the Developing VNet
1. **Create Developing VNet**:
   - Follow the steps to create a VNet.
   - Name: `DevelopingVNet`
   - Address space: `10.4.0.0/16`
   - Subnet: `DevelopingSubnet` with address range `10.4.1.0/24`

## Configure Hub-and-Spoke Architecture 🛞

### Step 1: Peer VNets with the Management VNet (HUB)
1. **Peer Management VNet with Production VNet**:
   - Navigate to `ManagementVNet`.
   - Select "Peerings" and click "Add".
   - Configure the peering with `ProductionVNet`.

2. **Peer Management VNet with Testing VNet**:
   - Follow the same steps to peer `ManagementVNet` with `TestingVNet`.

3. **Peer Management VNet with Developing VNet**:
   - Follow the same steps to peer `ManagementVNet` with `DevelopingVNet`.

### Step 2: Configure Network Security Groups (NSGs)
1. **Create NSGs for each VNet**:
   - Navigate to "Network Security Groups".
   - Create NSGs and associate them with subnets in each VNet as needed.
   - Configure rules to allow traffic between the VNets.

### Step 3: Configure Routing
1. **Enable IP Forwarding**:
   - Enable IP forwarding on the Management VNet to allow traffic to route between spoke VNets.

## Verify Connectivity 🏢

### Step 1: Launch VMs
1. **Create VMs in Each VNet**:
   - Create a VM in `ProductionSubnet`, `TestingSubnet`, and `DevelopingSubnet` using the same steps as previously.

### Step 2: Test Connectivity
1. **Ping from Management VM**:
   - SSH/RDP into the Management VM.
   - Use `ping` command to test connectivity to the VMs in `ProductionVNet`, `TestingVNet`, and `DevelopingVNet`.

Example Ping Commands:
```bash
ping <Production VM IP>
ping <Testing VM IP>
ping <Developing VM IP>
