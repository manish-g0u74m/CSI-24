# Create and test Azure Application gateway

## Overview
This guide will help you create and test an Azure Application Gateway to manage your web traffic. 

## Prerequisites
- An Azure account
- An existing Virtual Network (VNet) in Azure

## Resources
- [Azure Virtual Networks Overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [YouTube - Azure Application Gateway](https://www.youtube.com/watch?v=-SRk0hHa-S0)

## Steps

### 1. Create an Azure Application Gateway
1. **Navigate to the Azure Portal**:
    - Go to the [Azure Portal](https://portal.azure.com/).

2. **Create a New Application Gateway**:
    - Click "Create a resource".
    - Search for "Application Gateway" and select it.
    - Click "Create".

3. **Configure Basic Settings**:
    - **Subscription**: Select your Azure subscription.
    - **Resource Group**: Create a new resource group or select an existing one.
    - **Application Gateway Name**: Provide a name for your Application Gateway.
    - **Region**: Choose the region where you want to deploy the Application Gateway.

4. **Configure Frontend IP**:
    - **Frontend IP Configuration**: Choose between Public or Private IP.
    - If Public, select or create a new public IP address.

5. **Configure Backend Pools**:
    - Add your existing VMs or web servers to the backend pool.

6. **Configure Routing Rules**:
    - **Listener**: Create a new listener, set the protocol (HTTP or HTTPS), and configure the frontend port.
    - **Backend Target**: Select the backend pool created earlier.
    - **HTTP Settings**: Create a new HTTP setting or use an existing one. Configure settings such as session persistence, port, and protocol.

7. **Review and Create**:
    - Review your settings.
    - Click "Create" to deploy the Application Gateway.

### 2. Test the Azure Application Gateway
1. **DNS Configuration**:
    - If you have a domain, update your domain's DNS settings to point to the Application Gateway's public IP address.

2. **Verify Connectivity**:
    - Open a web browser and navigate to your domain or the public IP address of the Application Gateway.
    - Ensure that traffic is being correctly routed to the backend VMs or web servers.

### Conclusion
By following these steps, you will have created and tested an Azure Application Gateway to manage your web traffic effectively. 

### Additional Resources
- [Azure Virtual Networks Overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [YouTube - Azure Application Gateway](https://www.youtube.com/watch?v=-SRk0hHa-S0)

If you have any questions or need further assistance, feel free to ask!
