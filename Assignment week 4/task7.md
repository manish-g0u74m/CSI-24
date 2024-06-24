# Azure Application Gateway Guide ☁️

## Table of Contents 📋
1. [Introduction to Azure Application Gateway](#introduction-to-azure-application-gateway)
2. [Prerequisites](#prerequisites)
3. [Create a Virtual Network and Subnets](#create-a-virtual-network-and-subnets)
4. [Create the Application Gateway](#create-the-application-gateway)
5. [Configure Backend Pools](#configure-backend-pools)
6. [Configure Listeners and Rules](#configure-listeners-and-rules)
7. [Deploy Virtual Machines](#deploy-virtual-machines)
8. [Test the Application Gateway](#test-the-application-gateway)
9. [Additional Resources](#additional-resources)

## Introduction to Azure Application Gateway ⛩️

Azure Application Gateway is a web traffic load balancer that enables you to manage traffic to your web applications. It provides Layer 7 load balancing and is used to manage HTTP and HTTPS traffic.

## Prerequisites 👲🏻

1. Azure Subscription
2. Basic understanding of Azure Networking concepts

## Create a Virtual Network and Subnets 🌍

### Step 1: Create a Virtual Network
1. **Navigate to the Azure Portal**:
   - Go to [portal.azure.com](https://portal.azure.com/) and sign in with your Azure account.

2. **Create a Virtual Network**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "Virtual Network" and select it.
   - Click "Create".
   - Configure the virtual network:
     - Name: `AppGatewayVNet`
     - Address space: `10.0.0.0/16`
     - Subnets: 
       - `AppGatewaySubnet` with address range `10.0.1.0/24`
       - `BackendSubnet` with address range `10.0.2.0/24`
   - Click "Review + create" and then "Create".

## Create the Application Gateway 📡

### Step 1: Create the Application Gateway
1. **Navigate to Create a Resource**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "Application Gateway" and select it.
   - Click "Create".

2. **Configure the Application Gateway Basics**:
   - Name: `MyAppGateway`
   - Tier: Standard V2
   - Region: Choose your preferred region
   - Virtual network: `AppGatewayVNet`
   - Subnet: `AppGatewaySubnet`
   - Click "Next: Frontends".

3. **Configure Frontends**:
   - Frontend IP address type: Public
   - Public IP address: Create a new public IP address
   - Click "Next: Backends".

## Configure Backend Pools 🛰️

### Step 1: Add Backend Pool
1. **Configure Backend Pool**:
   - Click "Add a backend pool".
   - Name: `MyBackendPool`
   - Add backend targets (Virtual Machines, VM scale sets, or IP addresses).
   - Click "Add" and then "Next: Configuration".

## Configure Listeners and Rules 🧩

### Step 1: Configure Listeners
1. **Add a Listener**:
   - Click "Add a listener".
   - Name: `MyListener`
   - Frontend IP: Select the frontend IP configured earlier
   - Protocol: HTTP
   - Port: 80
   - Click "Add" and then "Next: Routing rules".

### Step 2: Configure Routing Rules
1. **Add a Routing Rule**:
   - Click "Add a rule".
   - Rule name: `MyRule`
   - Listener: Select `MyListener`
   - Backend target: Select `MyBackendPool`
   - Click "Add".

2. **Review and Create**:
   - Click "Review + create" and then "Create".

## Deploy Virtual Machines 🚀

### Step 1: Create Virtual Machines
1. **Deploy Two or More VMs**:
   - Create at least two VMs in the `BackendSubnet`. Ensure these VMs are configured to serve web traffic (e.g., running a web server like Apache or IIS).

### Step 2: Install and Configure Web Server
1. **Install Web Server**:
   - SSH or RDP into each VM.
   - Install a web server (Apache for Linux, IIS for Windows).

Example for Ubuntu:
```bash
sudo apt update
sudo apt install apache2 -y
echo "Welcome to VM1" | sudo tee /var/www/html/index.html
