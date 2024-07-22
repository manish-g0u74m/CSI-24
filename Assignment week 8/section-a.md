# Section A: Schedule a Daily Backup of VM at 3:00 AM using Vault
- Create a Recovery Services Vault:
```sh
az backup vault create --resource-group <ResourceGroupName> --name <RecoveryServicesVaultName> --location <Location>
```
- Configure Backup Policy:
  - Create a backup policy JSON file (e.g., backup-policy.json):
```json
{
  "name": "DailyBackupPolicy",
  "properties": {
    "schedulePolicy": {
      "scheduleRunFrequency": "Daily",
      "scheduleRunTimes": ["2023-03-01T03:00:00Z"]
    },
    "retentionPolicy": {
      "dailySchedule": {
        "retentionTimes": ["2023-03-01T03:00:00Z"],
        "retentionDuration": {
          "count": 30,
          "durationType": "Days"
        }
      }
    }
  }
}
```
- Apply the backup policy:
```sh
az backup policy create --resource-group <ResourceGroupName> --vault-name <RecoveryServicesVaultName> --policy '<backup-policy.json>'
```
- Enable Backup for VM:
```sh
az backup protection enable-for-vm --resource-group <ResourceGroupName> --vault-name <RecoveryServicesVaultName> --vm <VMName> --policy-name DailyBackupPolicy
```
