# Setting Up a Domain and DNS with Azure VM 📟

## Table of Contents 📋
1. [Introduction](#introduction)
2. [Set Up a Domain](#set-up-a-domain)
3. [Create a Virtual Machine](#create-a-virtual-machine)
4. [Configure DNS for Traffic Management](#configure-dns-for-traffic-management)
5. [Deploy a Web Server](#deploy-a-web-server)
6. [Verify Configuration](#verify-configuration)
7. [Additional Resources](#additional-resources)

## Introduction 📶

This guide provides step-by-step instructions on how to set up a domain, configure a server on an Azure VM, and use Azure DNS to manage traffic. 

## Set Up a Domain 🌍

### Step 1: Register a Domain
1. **Choose a Domain Registrar**:
   - Use a domain registrar such as GoDaddy, Namecheap, or any other preferred registrar.
   - Search for your desired domain name and register it.

### Step 2: Configure Domain with Azure DNS
1. **Navigate to the Azure Portal**:
   - Go to [portal.azure.com](https://portal.azure.com/) and sign in with your Azure account.

2. **Create a DNS Zone**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "DNS Zone" and select it.
   - Click "Create".
   - Configure the DNS zone:
     - Name: Enter your domain name (e.g., `example.com`).
     - Resource Group: Select or create a resource group.
   - Click "Review + create" and then "Create".

### Step 3: Update Registrar's Name Server Records
1. **Get Azure Name Servers**:
   - Navigate to the DNS zone you just created.
   - Copy the name servers listed in the "Name servers" section.

2. **Update Name Servers**:
   - Go to your domain registrar’s website.
   - Navigate to the DNS settings for your domain.
   - Replace the existing name servers with the Azure name servers you copied.

## Create a Virtual Machine 🖥️

### Step 1: Create a VM in Azure
1. **Navigate to the Azure Portal**:
   - Click "Create a resource" in the left-hand menu.
   - Search for "Virtual Machine" and select it.
   - Click "Create".

2. **Configure the Virtual Machine**:
   - Basics:
     - Resource Group: Select your resource group.
     - Virtual machine name: Enter a name (e.g., `webserver-vm`).
     - Region: Choose your preferred region.
     - Image: Choose an operating system (e.g., Ubuntu Server 20.04 LTS).
     - Size: Choose a VM size based on your requirements.
     - Authentication: Choose SSH public key or password for authentication.
   - Networking:
     - Virtual Network: Create or select an existing VNet.
     - Subnet: Create or select an existing subnet.
     - Public IP: Create a new public IP.
   - Click "Review + create" and then "Create".

## Configure DNS for Traffic Management 🚦

### Step 1: Create DNS Records
1. **Navigate to Your DNS Zone**:
   - In the Azure Portal, go to "All resources" and select your DNS zone.

2. **Add an A Record**:
   - Click "+ Record set".
   - Name: Enter a name (leave blank for root domain or enter "www" for www.example.com).
   - Type: Select `A`.
   - TTL: Set the TTL value (e.g., 3600 seconds).
   - IP Address: Enter the public IP address of your VM.
   - Click "OK".

## Deploy a Web Server 🌐

### Step 1: Install a Web Server on the VM
1. **SSH into Your VM**:
   - Use an SSH client (like PuTTY) or the Azure Cloud Shell to connect to your VM.

2. **Install a Web Server**:
   - For Ubuntu, install Apache:
     ```bash
     sudo apt update
     sudo apt install apache2 -y
     ```
   - For Windows, install IIS (use the built-in feature to enable IIS).

### Step 2: Configure the Web Server
1. **Create a Simple Web Page**:
   - Create an `index.html` file in the web server's root directory.
   - Example for Apache:
     ```bash
     echo "Welcome to my website" | sudo tee /var/www/html/index.html
     ```

## Verify Configuration ✅

### Step 1: Test Domain Resolution
1. **Access Your Website**:
   - Open a web browser.
   - Navigate to your domain (e.g., `http://example.com` or `http://www.example.com`).
   - You should see the web page you configured.

### Step 2: Test DNS Propagation
1. **Check DNS Records**:
   - Use tools like `nslookup`, `dig`, or online DNS propagation checkers to verify your DNS records are correctly set up and propagated.
