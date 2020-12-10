# Design Decisions

| Decision | Justification | Risks | Alternatives | Notes |
|-|-|-|-|-|
| All regions must support all customers | Customers may need to make services available in different geographies | Scale limits |-| IPSEC VPN for each customer between regions they are in (self-provisioned via vCD) |
| VM mobility is permitted within a Region, but not between Regions | Links between AZ are high speed low latency, where inter-region links are higher latency and slower | Customer workloads need to be well-architected to take advantage of this |-| Professional services available |
| A city has multiple datacenters, each datacenter is an Availability Zone, and a city forms a Region | Increased availability and mobility |-|-|-|
| One NSX Manager Cluster per Region | Each Region will have stretched network and security objects | NSX Federation scale is too low for future growth | NSX Federation |-|
| Stretch Networks between AZs in a Region | Shared Networks and Security policy |-|-|-|
| T0-T0 Aggregation | To avoid constantly updating BGP Neighbor configurations |-|-|-|
| Tenant Isolation | Tennants will receive a dedicated T1 router, and use DFW and gateway firewall at their own discretion |-|-| Professional services available |
| VDI Placement will be on the same Transport Zone and have a dedicated vn segment on the customers T1 | Security is the responsibility of the customer within their tenancy |-|-| Professional services available |
| IPSEC Tunnel overlays | Customers using both environments need access between Tiers and customers may need access to each other |-| Route Everything and Microsegment, Route Reflectors |-|
| NSX Edge VMs sized at Large | Large VM supports up to 40 tenants with a load balancer and BFD not needed | Higher average cost per VM | Bare Metal Edges | Allows a standard hardware form-factor for Edge hypervisors |
| Manage tenant to infrastructure ration in a scalable and maintainable way |-|-|-| Keep Edge Transport Node to tenant ratios low where possible |
|-|-|-|-|-|
