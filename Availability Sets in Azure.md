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
