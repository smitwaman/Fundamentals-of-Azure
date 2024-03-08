
Networking

●	CIDR: Used in virtual network configuration
○	Pattern : xxx.xxx.xxx.xxx/n

○	172.168.0.1/34 results in range from 172.168.1.0 to 172.168.1.255

○	A network security groupcontains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources.

●	Attributes of a network security group(NSG) ruleare as follows
○	Priority: Decides which rule will be checked first

○	Action: Allow/Deny

○	5-tuple

■	Source IP

■	Source Port

■	Destination IP

■	Destination Port

■	Protocol
 




Here's a step-by-step explanation with a JSON template for Networking terms:

1. Define CIDR:

```json
{
  "CIDR": {
    "Description": "CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing Internet Protocol packets.",
    "Usage": "Used in virtual network configuration.",
    "Pattern": "xxx.xxx.xxx.xxx/n",
    "Example": "172.168.0.1/34 results in a range from 172.168.1.0 to 172.168.1.255"
  }
}
```

2. Define Network Security Group (NSG):

```json
{
  "Network_Security_Group": {
    "Description": "A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources."
  }
}
```

3. Define attributes of an NSG rule:

```json
{
  "NSG_Rule_Attributes": {
    "Priority": {
      "Description": "Decides which rule will be checked first."
    },
    "Action": {
      "Description": "Allow/Deny."
    },
    "5-tuple": {
      "Description": "A set of five parameters defining network traffic.",
      "Parameters": [
        "Source IP",
        "Source Port",
        "Destination IP",
        "Destination Port",
        "Protocol"
      ]
    }
  }
}
```

Combine these steps into a single JSON template for a comprehensive explanation of Networking terms.
