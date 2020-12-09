# Scale Management

## Assumptions

Where applicable, we're considering NSX-T 3.0.2 for capacity purposes.

## NSX Manager Instances

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Edge Transport Node Clusters | 160 |
| Edge Transport Nodes | 320
| Compute Managers | 16 |
| Hypervisors | 1024 |
| Physical Servers | 300 |
| Compute Clusters | 128 |
| Hosts per Compute Cluster | 64 |
| Latency Between Manager Nodes | 10ms |
| Latency to Transport Nodes | 150ms |

## Tier-0 Routing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|

| BGP Peers | 640 |
| Prefix-lists | 500 |
| Prefix-list entries | 10 |
| Logical Routers| 160 |
| Subtending Tier-1 Logical Routers| 400 |

## Tier-1 Routing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Logical Routers | 4,000 | 1,500+ |
| Gateways per Compute Host | 1,000 |
| Max internal routes | 1,000 |
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
| Logical Ports | 25,000 |
| Stateful Rules | 100,000 |
| Rules Per Compute Host | 10,000 |

## Load Balancing

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| Small Load Balancer per M Node | 10 |
| Small Load Balancer per L Node | 40 |
| Small Load Balancer per XL Node | 80 |
| Small Load Balancer per BM Edge Node | 750 |
| vIPs per Small Load Balancer | 20 |

## VPN

| Feature | ConfigMax | Capacity Needed | Notes |
|-|:-:|:-:|-|
| IPSec L2L| Small 128 <br /> Medium 256 <br /> Large 512 <br /> XL 512 <br /> BM 512 | 400/Logical Router |

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
