# Section B: Create an Alert Rule for VM CPU Percentage
- Create an Action Group for Email Alerts:
```sh
az monitor action-group create --resource-group <ResourceGroupName> --name <ActionGroupName> --short-name <ActionGroupShortName> --email-receiver name=<YourName> email=<YourEmail>
```
- Create an Alert Rule for CPU Percentage:
``` sh
az monitor metrics alert create --resource-group <ResourceGroupName> --name "CPU
```
