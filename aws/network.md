# difference in VPC and VPN?

Amazon VPC allows you to create a logically isolated network within the AWS cloud. It provides control over network configuration, 
including IP address ranges, subnets, route tables, and network gateways.

2. Key Features:

**Isolated Network:** Create a private, isolated network environment in the AWS cloud.

**Subnets:** Divide your VPC into subnets (public and private) to control traffic flow and organization.

**Security Groups and Network ACLs:** Implement security measures at the instance level (Security Groups) and subnet level (Network ACLs).

**Route Tables:** Define how traffic is routed within your VPC and to/from the internet.

**Internet Gateway (IGW)**: Allows instances in public subnets to access the internet.

**NAT Gateway/Instance**: Allows instances in private subnets to access the internet while keeping them isolated from inbound traffic.

**VPC Peering:** Connects multiple VPCs within the same region.

**VPC Endpoints:** Allows private connections to AWS services without using public IPs.



**VPN (Virtual Private Network)**
1. Purpose: A VPN provides a secure, encrypted connection over a public network (such as the internet) to connect remote users
  or networks to a private network. It is commonly used to extend network access securely.
