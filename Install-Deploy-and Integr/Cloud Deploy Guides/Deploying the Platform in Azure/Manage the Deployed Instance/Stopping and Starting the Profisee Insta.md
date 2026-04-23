# Stopping and Starting the Profisee Instance

Because Azure Kubernetes Services deploys the Profisee Platform as a service, you have the ability to enable and disable your instance of Profisee to lower the cost of operation. This is especially useful in a non-production environment where the Platform does not need to be continually run. Note that this does not completely turn off all resources and operating costs. Some background resources and networking artifacts may continue to accrue minor costs.

There are two main resources you can stop and start at will to better manage operating costs: virtual machines, and the database.

### Virtual Machines

You can completely disable your virtual machines to turn off all operating costs. To prevent your virtual machines from running, you must de-allocate both your Linux and Windows VM using the following commands.

```
az vmss deallocate -g myResourceGroup -n myLinuxScaleSetName
az vmss deallocate -g myResourceGroup -n myWindowsScaleSetName
```

To re-allocate your VMs, use the following commands.

```
az vmss start -g myResourceGroup -n myLinuxScaleSetName
az vmss start -g myResourceGroup -n myWindowsScaleSetName
```

### Database

You cannot completely turn off your database. However, you can temporarily scale back the database to reduce operating costs. The following command causes your database to run in "basic edition," which continues to operate at a minimal level for a minor operating cost.

```
az sql db create -g myResourceGroup -s mySqlServerName -n dbName --edition Basic
```

The following command returns your database to its default operating capacity.

```
az sql db create -g myResourceGroup -s mySqlServerName -n dbName --edition GeneralPurpose --family Gen5 --capacity 2
```

### See more

[Automatically Start and Stop your Virtual Machines](https://docs.microsoft.com/en-us/azure/automation/automation-solution-vm-management-enable)