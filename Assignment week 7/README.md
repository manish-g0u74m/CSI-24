# Week - 7 : Azure Infrastructure
## Step-by-Step Guide
1. Observe Assigned Subscriptions
Resources:
[Azure CLI Documentation](https://www.youtube.com/watch?v=OQwQmikCLs4&pp=ygUWYXp1cmUgYWN0aXZlIGRpcmVjdG9yeQ%3D%3D)
```sh
# List all subscriptions
az account list --output table

# Set the default subscription
az account set --subscription "YOUR_SUBSCRIPTION_ID"
```

2. Observe Azure Entra ID or Create Own Azure Entra ID
Resources:
[Azure CLI Documentation](https://learn.microsoft.com/en-us/cli/azure/what-is-azure-cli)
```sh
# Observe Azure Entra ID (formerly Azure AD)
az ad signed-in-user show

# Create Azure Entra ID (If not already created, follow Azure portal guide)
```

3. Create Test Users and Groups
```sh
# Create a test user
az ad user create --display-name "Test User" --user-principal-name testuser@yourdomain.onmicrosoft.com --password TestPassword123!

# Create a test group
az ad group create --display-name "Test Group" --mail-nickname "testgroup"

# Add user to the group
az ad group member add --group "Test Group" --member-id $(az ad user show --id testuser@yourdomain.onmicrosoft.com --query objectId -o tsv)
```

4. Assign a RBAC Role to User and Test
```sh
# Assign the "Reader" role to a user at the subscription level
az role assignment create --assignee testuser@yourdomain.onmicrosoft.com --role "Reader" --scope /subscriptions/YOUR_SUBSCRIPTION_ID

# Verify the assignment
az role assignment list --assignee testuser@yourdomain.onmicrosoft.com --output table
```

5. Create a Custom Role and Assign to Users and Test
```sh
# Define a custom role in a JSON file (customRole.json)
cat <<EOF > customRole.json
{
  "Name": "Custom Role",
  "IsCustom": true,
  "Description": "Custom role for testing",
  "Actions": [
    "Microsoft.Resources/subscriptions/resourceGroups/read",
    "Microsoft.Resources/subscriptions/resourceGroups/write"
  ],
  "NotActions": [],
  "AssignableScopes": [
    "/subscriptions/YOUR_SUBSCRIPTION_ID"
  ]
}
EOF

# Create the custom role
az role definition create --role-definition customRole.json

# Assign the custom role to a user
az role assignment create --assignee testuser@yourdomain.onmicrosoft.com --role "Custom Role" --scope /subscriptions/YOUR_SUBSCRIPTION_ID

# Verify the assignment
az role assignment list --assignee testuser@yourdomain.onmicrosoft.com --output table
```

6. Create Virtual Machine and VNet from Azure CLI
Resources:
[Azure CLI Documentation]()https://www.youtube.com/watch?v=DOywwse_j8I
```sh
# Create a resource group
az group create --name TestResourceGroup --location eastus

# Create a virtual network
az network vnet create --resource-group TestResourceGroup --name TestVNet --address-prefix 10.0.0.0/16 --subnet-name TestSubnet --subnet-prefix 10.0.0.0/24

# Create a virtual machine
az vm create --resource-group TestResourceGroup --name TestVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys --vnet-name TestVNet --subnet TestSubnet
```

7. Create and Assign a Policy at Subscription Level
Resources:
[Azure Policy Documentation](https://www.youtube.com/watch?v=4wGns611G4w&pp=ygUMYXp1cmUgcG9saWN5)

```sh
# Create a policy definition (policyDefinition.json)
cat <<EOF > policyDefinition.json
{
  "if": {
    "allOf": [
      {
        "field": "location",
        "notIn": ["eastus"]
      }
    ]
  },
  "then": {
    "effect": "deny"
  }
}
EOF

# Create the policy
az policy definition create --name "DenyNonEastUS" --display-name "Deny non-East US locations" --description "Deny resources not in East US" --rules policyDefinition.json --mode All

# Assign the policy to the subscription
az policy assignment create --name "DenyNonEastUSAssignment" --display-name "Deny non-East US locations" --policy "DenyNonEastUS" --scope /subscriptions/YOUR_SUBSCRIPTION_ID
```

8. Create an Azure Key Vault and Store Secrets
Resources:
[Azure Key Vault Documentation](https://www.youtube.com/watch?v=JDRixckApxM&pp=ygUPYXp1cmUga2V5IHZhdWx0)
```sh
# Create a key vault
az keyvault create --name TestKeyVault --resource-group TestResourceGroup --location eastus

# Store a secret in the key vault
az keyvault secret set --vault-name TestKeyVault --name "TestSecret" --value "MySecretValue"
```
9. Configure Access Policies for the Key Vault
```sh
# Allow a user to manage secrets in the key vault
az keyvault set-policy --name TestKeyVault --upn testuser@yourdomain.onmicrosoft.com --secret-permissions get list set delete
```

10. Retrieve Secret from Key Vault Using Azure CLI
```sh
# Retrieve the secret value
az keyvault secret show --vault-name TestKeyVault --name TestSecret
```
11. Create a VM from PowerShell
Resources:
[Azure PowerShell Documentation](https://www.youtube.com/watch?v=-SRk0hHa-S0)
```powershell
# Connect to Azure
Connect-AzAccount

# Create a resource group
New-AzResourceGroup -Name TestResourceGroup -Location eastus

# Create a virtual network
$vnet = New-AzVirtualNetwork -ResourceGroupName TestResourceGroup -Location eastus -Name TestVNet -AddressPrefix 10.0.0.0/16
$subnetConfig = Add-AzVirtualNetworkSubnetConfig -Name TestSubnet -AddressPrefix 10.0.0.0/24 -VirtualNetwork $vnet
$vnet | Set-AzVirtualNetwork

# Create a virtual machine
$vmConfig = New-AzVMConfig -VMName TestVM -VMSize Standard_DS1_v2 | Set-AzVMOperatingSystem -Linux -ComputerName TestVM -Credential (Get-Credential) | Set-AzVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 18.04-LTS -Version latest | Add-AzVMNetworkInterface -Id (New-AzNetworkInterface -Name TestVM-NIC -ResourceGroupName TestResourceGroup -Location eastus -SubnetId $vnet.Subnets[0].Id).Id

New-AzVM -ResourceGroupName TestResourceGroup -Location eastus -VM $vmConfig
```
- This guide should help you complete the tasks you described. Make sure to replace placeholders like YOUR_SUBSCRIPTION_ID and yourdomain.onmicrosoft.com with your actual subscription ID and domain. If you have any questions or need further clarification, feel free to ask!









