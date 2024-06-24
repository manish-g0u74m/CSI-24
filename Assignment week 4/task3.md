# Azure Load Balancer Guide ⚖️

## Table of Contents 📋
1. [Introduction to Load Balancers](#introduction-to-load-balancers)
2. [Create an External Load Balancer](#create-an-external-load-balancer)
3. [Create an Internal Load Balancer](#create-an-internal-load-balancer)
4. [Verify Load Balancer Functionality](#verify-load-balancer-functionality)
5. [Additional Resources](#additional-resources)

## Introduction to Load Balancers 🗄️

Azure Load Balancer provides high availability and network performance to your applications. It distributes incoming network traffic across multiple backend resources or servers.

### Types of Load Balancers
- **External Load Balancer**: Balances traffic coming from the internet.
- **Internal Load Balancer**: Balances traffic within a virtual network.

## Create an External Load Balancer 🛠️

### Step 1: Create a Virtual Network and Subnets
1. **Navigate to the Azure Portal**:
   - Go to [portal.azure.com](https://portal.azure.com/) and sign in with your Azure account.

2. **Create a Virtual Network**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "Virtual Network" and select it.
   - Click "Create".
   - Configure the virtual network:
     - Name: `ExternalVNet`
     - Address space: `10.0.0.0/16`
     - Subnet: `ExternalSubnet` with address range `10.0.1.0/24`
   - Click "Review + create" and then "Create".

### Step 2: Create Virtual Machines
1. **Create Two or More VMs**:
   - Create at least two VMs in the `ExternalSubnet`. Ensure these VMs are part of the same availability set or VM scale set for high availability.

### Step 3: Create an External Load Balancer
1. **Create a Load Balancer**:
   - Navigate to "Create a resource" > "Networking" > "Load Balancer".
   - Configure the load balancer:
     - Name: `ExternalLoadBalancer`
     - Type: Public
     - SKU: Basic or Standard
     - Virtual Network: `ExternalVNet`
     - Subnet: `ExternalSubnet`
   - Click "Review + create" and then "Create".

### Step 4: Configure Backend Pool
1. **Configure Backend Pool**:
   - Navigate to your newly created load balancer.
   - Select "Backend pools" and click "Add".
   - Name: `ExternalBackendPool`
   - Add the VMs you created earlier.

### Step 5: Configure Health Probes
1. **Create Health Probes**:
   - Select "Health probes" and click "Add".
   - Name: `ExternalHealthProbe`
   - Protocol: HTTP
   - Port: 80
   - Path: `/`
   - Click "OK".

### Step 6: Configure Load Balancing Rules
1. **Create Load Balancing Rule**:
   - Select "Load balancing rules" and click "Add".
   - Name: `ExternalLoadBalancingRule`
   - Frontend IP address: `ExternalLoadBalancer`
   - Backend pool: `ExternalBackendPool`
   - Protocol: TCP
   - Port: 80
   - Backend port: 80
   - Health probe: `ExternalHealthProbe`
   - Click "OK".

## Create an Internal Load Balancer 🔧

### Step 1: Create a Virtual Network and Subnets
1. **Navigate to the Azure Portal**:
   - Use the same steps as above to create another virtual network.
   - Name: `InternalVNet`
   - Address space: `10.1.0.0/16`
   - Subnet: `InternalSubnet` with address range `10.1.1.0/24`

### Step 2: Create Virtual Machines
1. **Create Two or More VMs**:
   - Create at least two VMs in the `InternalSubnet`.

### Step 3: Create an Internal Load Balancer
1. **Create a Load Balancer**:
   - Navigate to "Create a resource" > "Networking" > "Load Balancer".
   - Configure the load balancer:
     - Name: `InternalLoadBalancer`
     - Type: Internal
     - SKU: Basic or Standard
     - Virtual Network: `InternalVNet`
     - Subnet: `InternalSubnet`
   - Click "Review + create" and then "Create".

### Step 4: Configure Backend Pool
1. **Configure Backend Pool**:
   - Navigate to your newly created load balancer.
   - Select "Backend pools" and click "Add".
   - Name: `InternalBackendPool`
   - Add the VMs you created earlier.

### Step 5: Configure Health Probes
1. **Create Health Probes**:
   - Select "Health probes" and click "Add".
   - Name: `InternalHealthProbe`
   - Protocol: HTTP
   - Port: 80
   - Path: `/`
   - Click "OK".

### Step 6: Configure Load Balancing Rules
1. **Create Load Balancing Rule**:
   - Select "Load balancing rules" and click "Add".
   - Name: `InternalLoadBalancingRule`
   - Frontend IP address: `InternalLoadBalancer`
   - Backend pool: `InternalBackendPool`
   - Protocol: TCP
   - Port: 80
   - Backend port: 80
   - Health probe: `InternalHealthProbe`
   - Click "OK".

## Verify Load Balancer Functionality 👨‍💻

### Step 1: Verify External Load Balancer
1. **Get Public IP Address**:
   - Navigate to the `ExternalLoadBalancer`.
   - Copy the public IP address.
   - Open a web browser and navigate to the public IP address. You should see the default page of one of the VMs.

### Step 2: Verify Internal Load Balancer
1. **Get Internal IP Address**:
   - Navigate to the `InternalLoadBalancer`.
   - Copy the internal IP address.
   - From another VM within the same virtual network, open a web browser and navigate to the internal IP address. You should see the default page of one of the VMs.
