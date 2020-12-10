# Design Decisions

| Decision | Justification | Implication | Risks | Alternatives | Notes |
|-|-|-|-|-|-|
| A city has 2 datacenters, and a city forms a Pod | Increased availability and mobility |-| VM mobility is permitted within a Pod, but not between Pods |-|-|
| Use NSX Federation | Share networks and security objects between datacenters | - | Scale limits | - | - |
| Stretch Networks between AZs in a Pod | Shared Networks and Security policy |-|-|-|-|
| BGP Neighbor Range | To avoid constantly updating BGP Neighbor configurations |-|-|-|-|
| IPSEC Tunnels between Tier-3 and Tier-2 | Customers using both environments need access between Tiers |-|-| Route Everything and Microsegment, Route Reflectors |-|
| Tenant Isolation | Tier-2 tenants will be in NATed T1s, Tier-3 tenants will use DFW and Gateway FW on T0 |-|-|-|-|
| Something about Edge design -|-|-|-|-|-|
| XL or BM Edge?? |-|-|-|-|-|
|-|-|-|-|-|-|
|-|-|-|-|-|-|
