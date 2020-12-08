# Requirements, Decision, Justification, Implications

| Name | Requirement | Decision | Justification | Implications | Notes |
|-|-|-|-|-|-|
| Requirement 1 | Security is paramount. We need to protect our tenants’ applications from internal and external threats. | We'll consider Tier-1 Stateful Services sufficient, as long as general services like internet egress pin through a dedicated appliance or customer premise | Customers can manage their own N-S security chains through vCD using NSX-T native constructs.| Customers may prefer using their own vendor-proprietary services at the edge.|
| Requirement 2 | The solution must scale beyond 1500 tenants | Multiple NSX-T Manager instances are required <br /> A repeatable Edge Transport Node Cluster blueprint is compulsory. | Dedicated compute instances can be peeled off from the general pool, but a more scalable solution is required for shared tenancy. | More cost for dedicated customers (but they're probably already paying it for V) <br /> ConfigMax: 400 T1s per LR, 1000 T1s per ETN <br /> Breakout based on tier? <br> AZ? Region? |
| Requirement 3 | We must be able to provide integration with external security solutions for some of our tenants (Palo Alto, etc..) | Service Insertion w/ Partners is mandatory | This doesn't cost as much as V, and will probably be an easy value add | Customers may have difficulty getting used to vwire deployments if they don't already use them |
| Requirement 4 | Tenants Should only have access and visibility to their applications and self-service provisioning and management, where necessary, but not to those of other tenants. | vCD RBAC - use vCD as your front door, everywhere. | vCD will allow for the granular RBAC required here. |
| Requirement 5 | Adhere to regulatory compliance in the markets we provide services and for the verticals we serve. | vRNI may be a good fit for security controls, but vCD may need to provide additional capability here. | |
| Requirement 6 | Centralized Management is mandatory. The existing physical security mechanism is no longer scalable. | vCD RBAC - use vCD as your front door, everywhere. | | We're assuming physical means hardware network security |
| Requirement 7 | For some of our customers with compliance requirements, we need to provide security via 3rd party appliances. We also need to provide endpoint protection for these tenants | Service Insertion w/ Partners |
| Requirement 8 | Our data center design uses the availability zone model. In each city where we provide services, we have 2 or more data centers within a 10-mile radius to account for site failures. The solution should allow for streamline mobility of tenant workloads without the need to reconfigure networking or security policies | AZ -> NSX Manager mapping? |
| Requirement 9 | Reduce dependence on physical security appliances. Most network and security services should be deployed through software. | Migrate E-W firewalling to T1s, DFW | $$$ |
| Requirement 10 | Possible 3rd party integration. The security policies leveraged should be easily modifiable to seamlessly integrate 3rd party products. We need the flexibility to only license and deploy 3rd party security appliances as needed. | Service Insertion w/ Partners |
| Requirement 11 | All tenants will require access to shared services we provide (AD, DNS, NTP) |
| Requirement 12 | Shared services must have a 99.99% uptime |
| Requirement 13 | The security Posture of all workloads must remain consistent even as the move from site to site. This must happen without any additional administrative overhead |
| Requirement 14 | We need to provide tenants in both our shared and dedicated IaaS solution access to enhanced security services if desired. |
| Requirement 15 | The solution needs to scale beyond 1500 tenants with 5% or less of those tenants using our dedicated IaaS solution |
| Requirement 16 | Due to security requirements, dedicated tenants cannot share T0 gateways with other tenants |
| Requirement 17 | Dedicated IaaS tenants are provided access to both our VDI solution and site-to-site VPN as a value-added service |
| Requirement 18 | Tenants must be isolated from one another. One tenant should not be allowed access to other tenants |
| Requirement 19 | All tenants must have access to shared services provided by ZCS |
| Requirement 20 | The solution must minimize administrative overhead |
| Requirement 21 | Route-based VPN must be used for site-to-site VPN configuration from tenants’ dedicated IaaS and their on-premise datacenter |
| Requirement 22 | All Tenant applications need communication with Shared services provided by ZCS (AD, DNS, and NTP services, etc…). These services are running in the Physical infrastructure on bare metal servers. |
| Requirement 23 | Tenants should have external access to their applications on port 443. |
| Requirement 24 | Tenants with enhanced performance and security requirements will access their apps via a Horizon VDI running in a dedicated VDI cluster in the environment. This VDI pool is a shared (Floating) Pool and should be accessible to all users who have subscribed to the solution via their browser and the Horizon View Client |
| Requirement 25 | From the Shared VDI environment, admin users should have HTTP, HTTPS, SSH RDP, and VNC access to their virtual machines. |
| Requirement 26 | Future-proof the deployment for 3rd party guest introspection. We are looking at 3rd party guest introspection services. We need the infrastructure to be prepared for integrating the 3rd party product in the future. We also want the consultant to create a policy to consume this 3rd party product once it is deployed. |
| Requirement 27 | With potentially multiple virtual routers the solution should minimize the need to update BGP neighbor configuration every time a new T0 gateway is deployed |
