# Azure Application Gateway Guide ⛩️

## Table of Contents 📋
1. [Introduction to Azure Application Gateway](#introduction-to-azure-application-gateway)
2. [Create an Application Gateway](#create-an-application-gateway)
3. [Configure Backend Pools](#configure-backend-pools)
4. [Configure Listeners and Rules](#configure-listeners-and-rules)
5. [Deploy Virtual Machines](#deploy-virtual-machines)
6. [Test the Application Gateway](#test-the-application-gateway)
7. [Additional Resources](#additional-resources)

## Introduction to Azure Application Gateway 🎋

Azure Application Gateway is a web traffic load balancer that enables you to manage traffic to your web applications. Application Gateway provides Layer 7 load balancing and is used to manage HTTP and HTTPS traffic.

## Create an Application Gateway 🏯

### Step 1: Create a Virtual Network and Subnets
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

### Step 2: Create the Application Gateway
1. **Create an Application Gateway**:
   - Navigate to "Create a resource" > "Networking" > "Application Gateway".
   - Configure the application gateway:
     - Name: `MyAppGateway`
     - Region: Choose your preferred region.
     - Tier: Standard V2
     - Virtual Network: `AppGatewayVNet`
     - Subnet: Select `AppGatewaySubnet`
     - Configuration: Leave default settings for now.
   - Click "Review + create" and then "Create".

## Configure Backend Pools ↩️

### Step 1: Create Backend Pool
1. **Add Backend Pool**:
   - Navigate to your newly created application gateway.
   - Select "Backend pools" and click "Add".
   - Name: `MyBackendPool`
   - Add backend targets (Virtual Machines, VM scale sets, or IP addresses).

## Configure Listeners and Rules 🧾

### Step 1: Configure Listeners
1. **Add a Listener**:
   - Select "Listeners" and click "Add listener".
   - Name: `MyListener`
   - Frontend IP: Public or Private as per your requirement.
   - Port: 80 (HTTP) or 443 (HTTPS)
   - Click "OK".

### Step 2: Configure Rules
1. **Add a Rule**:
   - Select "Rules" and click "Add rule".
   - Name: `MyRule`
   - Listener: Select `MyListener`
   - Backend target: Select `MyBackendPool`
   - Click "OK".

## Deploy Virtual Machines 🖥️

### Step 1: Create Virtual Machines
1. **Deploy Two or More VMs**:
   - Create at least two VMs in the `BackendSubnet`. Ensure these VMs are configured to serve web traffic (e.g., running a web server like Apache or IIS).

### Step 2: Install and Configure Web Server
1. **Install Web Server**:
   - SSH or RDP into each VM.
   - Install a web server (Apache for Linux, IIS for Windows).
   - Configure the web server to serve a simple webpage.

Example for Ubuntu:
```bash
sudo apt update
sudo apt install apache2 -y
echo "Welcome to VM1" | sudo tee /var/www/html/index.html
