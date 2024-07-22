# Week - 8 : Azure Infrastructure
## Azure Backup and Alerts Configuration

### Overview
This repository contains scripts to configure daily backups for an Azure VM and set up alert rules for CPU usage.

### Prerequisites
- Azure CLI installed
- Appropriate Azure permissions

### Steps

1. Clone the repository.
2. Configure the scripts with your specific Azure resource details.
3. Run the scripts to set up backups and alerts.

### Scripts

- `create-backup.sh`: Creates a Recovery Services Vault, configures a backup policy, and enables backup for a VM.
- `create-alert.sh`: Creates an action group for email alerts and sets up an alert rule for VM CPU percentage.
- `backup-center.sh`: Sets up the Backup Center and provisions backups.

### Usage

```sh
# Schedule a daily backup of a VM at 3:00 AM using vault
./create-backup.sh

# Create an alert rule for VM CPU percentage
./create-alert.sh

# Provision backups in Backup Center
./backup-center.sh
```

### create-backup.sh

```sh
#!/bin/bash

# Variables
RESOURCE_GROUP="<ResourceGroupName>"
VAULT_NAME="<RecoveryServicesVaultName>"
LOCATION="<Location>"
VM_NAME="<VMName>"
POLICY_FILE="backup-policy.json"

# Create Recovery Services Vault
az backup vault create --resource-group $RESOURCE_GROUP --name $VAULT_NAME --location $LOCATION

# Create Backup Policy
az backup policy create --resource-group $RESOURCE_GROUP --vault-name $VAULT_NAME --policy @$POLICY_FILE

# Enable Backup for VM
az backup protection enable-for-vm --resource-group $RESOURCE_GROUP --vault-name $VAULT_NAME --vm $VM_NAME --policy-name DailyBackupPolicy
```

### create-alert.sh
```
#!/bin/bash

# Variables
RESOURCE_GROUP="<ResourceGroupName>"
ACTION_GROUP_NAME="<ActionGroupName>"
ACTION_GROUP_SHORT_NAME="<ActionGroupShortName>"
VM_RESOURCE_ID="<VMResourceID>"
EMAIL="<YourEmail>"
YOUR_NAME="<YourName>"

# Create Action Group for Email Alerts
az monitor action-group create --resource-group $RESOURCE_GROUP --name $ACTION_GROUP_NAME --short-name $ACTION_GROUP_SHORT_NAME --email-receiver name=$YOUR_NAME email=$EMAIL

# Create Alert Rule for CPU Percentage
az monitor metrics alert create --resource-group $RESOURCE_GROUP --name "CPU_Percentage_Alert" --scopes $VM_RESOURCE_ID --condition "avg Percentage CPU > 80" --description "Alert when CPU percentage exceeds 80%" --action-group $ACTION_GROUP_NAME
```

### backup-center.sh
```
#!/bin/bash

# Variables
RESOURCE_GROUP="<ResourceGroupName>"
BACKUP_CENTER_NAME="<BackupCenterName>"

# Create Backup Center
az backup center create --resource-group $RESOURCE_GROUP --name $BACKUP_CENTER_NAME

# Schedule a Daily Backup of VM at 3:00 AM using vault
./create-backup.sh
```

- By following these steps and using the provided scripts, you can configure daily backups for your VM and set up alert rules for CPU usage efficiently.

