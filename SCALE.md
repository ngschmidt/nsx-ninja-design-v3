# Scale Management

## Assumptions

Where applicable, we're considering NSX-T 3.0.2 for capacity purposes.

## NSX Manager Instances

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Edge Transport Node Clusters | 160 | 41 |
| Edge Transport Nodes | 320 | 123 | AZ Pod will consume 8 (AZ Aggregation) + 16 (4 per 400 Customers, enumerated to 1600) at T0 <br /> Total T0 per Region: 48 <br /> Tier-0 will have 8-way (Agg) and 4-way ETNCs <br /> Tier-1 will be 40:1 for 2-way A/P ETNCs <br /> Total T0+T1 Per Region: 123 for 1500 Clients |
| Compute Managers | 16 |
| Hypervisors | 1024 |
| Physical Servers | 300 |
| Compute Clusters | 128 |
| Hosts per Compute Cluster | 64 |
| Latency Between Manager Nodes | 10ms | Splitting NSX MGR Cluster Across AZs will be within this limit |
| Latency to Transport Nodes | 150ms | Constraining NSX MGR to a "Region(City)" will meet this requirement. |

## Tier-0 Routing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| BGP Peers | 640 | T0 Agg: 18 <br /> T0 Pod: 8 |
| Prefix-lists | 500 | <10 | Minimal in NAT environment |
| Prefix-list entries | 10 |
| Logical Routers| 160 | 3/AZ |
| Subtending Tier-1 Logical Routers| 400 | 400 | 40 per ETNC for T1 capacity (Large Size) will indicate 10 ETNCs per Pod. <br /> 11 ETNCs Per Pod Total |

## Tier-1 Routing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Logical Routers | 4,000 | 1,500+ |
| Gateways per Compute Host | 1,000 | 400-1500 | Capacity limits will likely grow ahead of ZCS given growth estimates. |
| Max internal routes | 1,000 | <10 |
| NAT Sessions per Edge Node | 4,000,000 |

## Firewall (N-S)

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Groups | 15,000 (10 per customer) |
| AD Groups | 100,000 |
| AD Users | 100,000 |
| Rules| 5,000 per Logical Router |

## Firewall (Distributed)

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Logical Ports | 25,000 | 15,000 |
| Stateful Rules | 100,000 |
| Rules Per Compute Host | 10,000 |

## Load Balancing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Small Load Balancer per M Node | 10 |
| Small Load Balancer per L Node | 40 | 1 | Per host as a scale option, not explicitly required |
| Small Load Balancer per XL Node | 80 |
| Small Load Balancer per BM Edge Node | 750 |
| vIPs per Small Load Balancer | 20 |

## VPN

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| IPSec L2L| Small 128 <br /> Medium 256 <br /> Large 512 <br /> XL 512 <br /> BM 512 | 400/Logical Router | Large VM Nodes will be the de-facto choice here. <br /> T0s may need to be re-sized. |

## Service Insertion (N-S)

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Services | 4 |
| SVMs | 200 |
| Rules | 10,000 |

## Service Insertion (Distributed)

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Logical Ports | 10,000 |
| Hosts with active Network Introspection | 256 |
| Service Insertion Policies per Compute Host | 100 |
| Services | 8 |
| Chains | 24 |
| SVMs | 72 |
| Redirection Rules | 10,000 |

## Guest Introspection|

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| App VMs per Compute Host | 40 |
| VMs per Compute Host | 256 |
| VMs | 7,500 |

## D-IDS

Not really viable here.

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Compute Hosts | 256 |

## vCD

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| vCenter | 35 | 9 | 9 Cities, 18+ AZs total. 1 Compute Manager per Region |
| NSX-T Managers | 30 | 9 |
| Organizations | 10,000 | 1,500 |
| External Networks | 8,000 | 1,500-4,500 | Assumes 3 per customer average |
| Universal Logical Routers | 1 Universal Router per VDC Group | `Shared Pod` |
| Latency from Cell to managed nodes | 150ms | | Map estimates are <100ms |
| Latency between Cells | 1ms | | Cells should be in the same Availability Zone hosted in the `Shared Pod`
