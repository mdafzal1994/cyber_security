NACL and Security group are stateless or stateful 

In AWS, **Network ACLs (NACLs)** and **Security Groups** serve different roles in network security and operate in distinct ways regarding their statefulness.

### Network ACLs (NACLs)

**1. Stateless:**
- **Behavior:** NACLs are stateless, meaning they do not track the state of connections. Each rule is evaluated independently for both inbound and outbound traffic.
- **Rule Application:** You must explicitly define rules for both inbound and outbound traffic. For example, if you allow inbound traffic on port 80, you must also create a rule to allow outbound traffic on port 80 if that traffic is required.
- **Default Behavior:** When an incoming request matches a rule allowing traffic, it doesn’t automatically allow the corresponding outbound response unless a separate outbound rule also allows it.
- **Use Case:** NACLs are typically used for controlling traffic at the subnet level within a VPC. They provide an additional layer of security by applying rules to all traffic entering and leaving a subnet.

### Security Groups

**1. Stateful:**
- **Behavior:** Security Groups are stateful. They automatically track the state of active connections and apply rules accordingly.
- **Rule Application:** If you allow inbound traffic on port 80 from a specific IP address, the response traffic is automatically allowed, even if there is no explicit outbound rule permitting it.
- **Default Behavior:** Security Groups automatically handle response traffic for allowed inbound requests, simplifying rule management and ensuring that connections are properly established and maintained.
- **Use Case:** Security Groups are used to control traffic at the instance level within a VPC. They provide a more granular level of security by applying rules to the traffic allowed to and from individual instances.



