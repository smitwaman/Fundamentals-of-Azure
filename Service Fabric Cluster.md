Here's a basic JSON template to deploy a Service Fabric Cluster:

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.ServiceFabric/clusters",
      "apiVersion": "2020-03-01-preview",
      "name": "myServiceFabricCluster",
      "location": "East US",
      "properties": {
        "managementEndpoint": "https://myclusterlocation.management.azure.com:19080",
        "nodeTypes": [
          {
            "name": "nt1",
            "applicationPorts": {
              "startPort": 20000,
              "endPort": 30000
            },
            "ephemeralPorts": {
              "startPort": 49152,
              "endPort": 65534
            },
            "httpGatewayEndpointPort": 19080,
            "isPrimary": true,
            "vmInstanceCount": 5
          }
        ],
        "vmImage": "Windows",
        "upgradeMode": "Automatic"
      }
    }
  ]
}
```

Explanation:
- `$schema`, `contentVersion`, `resources`: Standard properties for an Azure Resource Manager template.
- `type`: Specifies the resource provider namespace and resource type. For a Service Fabric Cluster, it's "Microsoft.ServiceFabric/clusters".
- `apiVersion`: Specifies the API version to use for the resource.
- `name`: Specifies the name of the Service Fabric Cluster.
- `location`: Specifies the Azure region where the Service Fabric Cluster will be deployed.
- `properties`: Additional properties of the Service Fabric Cluster.
  - `managementEndpoint`: Specifies the endpoint for managing the cluster.
  - `nodeTypes`: Specifies the configuration for the nodes in the cluster.
    - `name`: Specifies the name of the node type.
    - `applicationPorts`: Specifies the range of application ports.
    - `ephemeralPorts`: Specifies the range of ephemeral ports.
    - `httpGatewayEndpointPort`: Specifies the port used for the HTTP gateway endpoint.
    - `isPrimary`: Specifies if this node type is primary.
    - `vmInstanceCount`: Specifies the number of VM instances for this node type.
  - `vmImage`: Specifies the VM image to use for the cluster nodes.
  - `upgradeMode`: Specifies the upgrade mode for the cluster.

This JSON template can be used to deploy a Service Fabric Cluster in Azure with specified configurations for node types, VM image, and upgrade mode.
