# Set up a domain, setup a server on a VM and use the DNS server for traffic
## Overview
This guide will help you set up a domain, configure a server on an Azure Virtual Machine (VM), and use the DNS server for routing traffic. 

## Prerequisites
- An Azure account
- A domain purchased from a domain registrar (e.g., GoDaddy, Namecheap)

## Resources
- [Azure Virtual Networks Overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [YouTube - Azure Private Link](https://www.youtube.com/watch?v=57ZwdztCx2w)

## Steps

### 1. Purchase and Configure a Domain
1. **Purchase a Domain**: Choose a domain registrar like GoDaddy, Namecheap, or Google Domains, and purchase a domain.
2. **Log in to Your Domain Registrar**: Access your domain's DNS settings.

### 2. Create and Set Up an Azure Virtual Machine (VM)
1. **Create a Virtual Machine in Azure**:
    - Go to the [Azure Portal](https://portal.azure.com/).
    - Click on "Create a resource".
    - Select "Virtual Machine" under the "Compute" section.
    - Fill in the required details:
        - **Subscription**: Select your Azure subscription.
        - **Resource Group**: Create a new resource group or use an existing one.
        - **VM Name**: Provide a name for your VM.
        - **Region**: Choose a region.
        - **Image**: Select an OS image (e.g., Ubuntu, Windows Server).
        - **Size**: Choose a VM size based on your requirements.
    - Set up the admin credentials:
        - **Authentication Type**: Choose SSH public key for Linux or Password for Windows.
        - **Username**: Create a username.
        - **Password/SSH Key**: Enter a strong password or upload an SSH key.
    - Configure the disk settings (default options are usually sufficient).
    - Configure networking settings:
        - **Virtual Network**: Create a new virtual network or use an existing one.
        - **Subnet**: Select or create a subnet.
        - **Public IP**: Ensure that a public IP address is assigned.
    - Review your settings and click "Create".

2. **Connect to the VM**:
    - **Windows VM**: Use Remote Desktop Protocol (RDP) to connect.
    - **Linux VM**: Use SSH to connect (e.g., `ssh username@public-ip-address`).

### 3. Configure DNS for Traffic
1. **Find the Public IP of Your VM**: In the Azure Portal, navigate to your VM and locate its public IP address.
2. **Update DNS Records**:
    - Log in to your domain registrar.
    - Access the DNS settings for your domain.
    - Create an A record pointing to your VM's public IP address:
        - **Host**: @ (this represents the root domain).
        - **Points to**: [Your VM's Public IP]
        - **TTL**: Set a desired TTL value (default is usually fine).

## Conclusion
By following these steps, you will have a domain set up, a server running on an Azure VM, and DNS configured to route traffic to your VM. 

## Additional Resources
- [Azure Virtual Networks Overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [YouTube - Azure Private Link](https://www.youtube.com/watch?v=57ZwdztCx2w&pp=ygUSYXp1cmUgcHJpdmF0ZSBsaW5r)
