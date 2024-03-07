Availability Sets in Azure

●	An Update Domainand a Fault Domainis assigned to each VM in an Availability Zone
●	Fault domains define the group of virtual machines that share a common power source and network switch

●	Update domains are used for patching of the virtual machines. All virtual machines within an update domain will reboot together.

●	By default Availability Sets have two Fault Domains, each sharing a common power source and network switch, and VMs are automatically separated across the Fault Domains.

●	The number of Fault Domains in an Availability Set isn't exact, and the only guarantee that not all the VMs in the set will fail together.

●	Availability Sets are assigned five Update Domains, and VMs are grouped into these Update Domains automatically.

●	When a sixth VM is added to an Availability Set, it is assigned to the first Update Domain, and the seventh VM to the second Update Domain, etc. So the first and the sixth VMs added to an Availability Set could be rebooted at the same time in the instance of a planned maintenance event.

●	Only one Update Domain is ever rebooted at a time, but the reboot order isn't necessarily sequential, so the fifth Update Domain could be rebooted before the first.
●	Horizontal Scaling- The auto scale feature of Azure Monitor only scales horizontally, which is an increase ("out") or decrease ("in") of the number of VMs

●	Virtual Scaling- Vertical scaling keeps the same number of VMs, but makes the more 'up") or less ("down") powerful. Power is measured in attributes such as memory, CPU speed, or disk space. Vertical scaling is dependent on the availability of larger hardware, which quickly hits an upper limit and can vary by region.

●	Azure virtual machine scale sets let you create a set of identical load-balanced VMs which can be set to automatically scale up or scale down depending on requirements or a defined schedule.


To deploy Azure Virtual Machines with Availability Sets using a JSON template, follow these step-by-step instructions:

1. **Define the ARM Template**: Create a JSON file that defines the infrastructure resources including the Availability Set. Below is a simplified example of an ARM template:

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "availabilitySetName": {
      "type": "string",
      "defaultValue": "myAvailabilitySet",
      "metadata": {
        "description": "Name of the Availability Set"
      }
    },
    "vmName": {
      "type": "string",
      "defaultValue": "myVM",
      "metadata": {
        "description": "Name of the virtual machine"
      }
    },
    "region": {
      "type": "string",
      "defaultValue": "eastus",
      "metadata": {
        "description": "Region where the VM will be deployed"
      }
    }
  },
  "resources": [
    {
      "type": "Microsoft.Compute/availabilitySets",
      "apiVersion": "2021-03-01",
      "name": "[parameters('availabilitySetName')]",
      "location": "[parameters('region')]",
      "properties": {
        "platformFaultDomainCount": 2,
        "platformUpdateDomainCount": 5
      }
    },
    {
      "type": "Microsoft.Compute/virtualMachines",
      "apiVersion": "2021-03-01",
      "name": "[parameters('vmName')]",
      "location": "[parameters('region')]",
      "dependsOn": [
        "[resourceId('Microsoft.Compute/availabilitySets', parameters('availabilitySetName'))]"
      ],
      "properties": {
        "availabilitySet": {
          "id": "[resourceId('Microsoft.Compute/availabilitySets', parameters('availabilitySetName'))]"
        },
        "hardwareProfile": {
          "vmSize": "Standard_DS1_v2"
        },
        "osProfile": {
          "computerName": "[parameters('vmName')]",
          "adminUsername": "adminUser",
          "adminPassword": "Admin@123456"
        },
        "storageProfile": {
          "imageReference": {
            "publisher": "MicrosoftWindowsServer",
            "offer": "WindowsServer",
            "sku": "2019-Datacenter",
            "version": "latest"
          },
          "osDisk": {
            "createOption": "FromImage"
          }
        },
        "networkProfile": {
          "networkInterfaces": [
            {
              "id": "[resourceId('Microsoft.Network/networkInterfaces', variables('nicName'))]"
            }
          ]
        }
      }
    }
  ]
}
```

2. **Parameters**: Define parameters such as the name of the Availability Set, VM, and region.

3. **Availability Set**: Create an Availability Set resource specifying the number of fault domains (2 by default) and update domains (5 by default).

4. **Virtual Machine Configuration**: Configure the virtual machine properties, including associating it with the Availability Set.

5. **Deployment**: Deploy the ARM template using Azure CLI, PowerShell, or Azure Portal. Provide parameter values during deployment.

By following these steps, you can deploy Azure Virtual Machines with Availability Sets using a JSON template, ensuring fault tolerance and update management within your application.
