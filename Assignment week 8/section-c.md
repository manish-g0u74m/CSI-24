# Section C: Provision Backups in Backup Center
- Navigate to the Backup Center:
```sh
az backup center create --resource-group <ResourceGroupName> --name <BackupCenterName>
```
- Schedule a Daily Backup of VM at 3:00 AM:
  - Reuse the steps from Section A to configure a daily backup policy and enable backup for the VM.
