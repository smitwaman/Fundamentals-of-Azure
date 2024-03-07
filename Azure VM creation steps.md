To create an Azure Virtual Machine using a JSON template, follow these steps:

1. **Define the Azure Resource Manager (ARM) Template**: Create a JSON file that defines the infrastructure resources you want to deploy. Below is a sample template with explanations for each section:

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
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
    },
    "osType": {
      "type": "string",
      "defaultValue": "Windows",
      "allowedValues": [
        "Windows",
        "Linux"
      ],
      "metadata": {
        "description": "Operating System type for the VM (Windows/Linux)"
      }
    },
    "availabilityZone": {
      "type": "string",
      "defaultValue": "1",
      "allowedValues": [
        "1",
        "2",
        "3"
      ],
      "metadata": {
        "description": "Availability Zone for the VM"
      }
    }
  },
  "resources": [
    {
      "type": "Microsoft.Compute/virtualMachines",
      "apiVersion": "2021-03-01",
      "name": "[parameters('vmName')]",
      "location": "[parameters('region')]",
      "properties": {
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
      },
      "resources": [
        {
          "type": "Microsoft.Network/networkInterfaces",
          "apiVersion": "2021-03-01",
          "name": "[variables('nicName')]",
          "location": "[parameters('region')]",
          "properties": {
            "ipConfigurations": [
              {
                "name": "ipconfig1",
                "properties": {
                  "subnet": {
                    "id": "[variables('subnetRef')]"
                  },
                  "privateIPAllocationMethod": "Dynamic",
                  "publicIPAddress": {
                    "id": "[variables('publicIPAddressID')]"
                  }
                }
              }
            ]
          }
        }
      ]
    }
  ]
}
```

2. **Parameters**: Define the parameters required for deployment such as VM name, region, OS type, and availability zone.

3. **Resources**: Define the resources to be deployed, including the virtual machine, network interfaces, and other related components.

4. **Virtual Machine Configuration**: Configure the virtual machine properties such as hardware profile, OS profile, and storage profile. Specify the image reference for the OS.

5. **Network Interface Configuration**: Configure the network interface for the virtual machine. Specify the subnet, IP allocation method, and public IP address.

6. **Deployment**: Deploy the ARM template using Azure CLI, PowerShell, or Azure Portal. Use the parameters file to provide parameter values during deployment.

By following these steps, you can create an Azure Virtual Machine using a JSON template with the specified region, OS, availability zone, and other related components.
