# Scale Management

## Assumptions

Where applicable, we're considering NSX-T 3.0.2 for capacity purposes.

## NSX Manager Instances

- Edge Transport Node Clusters: 160
- Edge Transport Nodes: 320
- Compute Managers: 16
- Hypervisors: 1024
- Physical Servers: 300
- Compute Clusters: 128
- Hosts per Compute Cluster: 64
- Latency Between Manager Nodes: 10ms
- Latency to Transport Nodes: 150ms

## Tier-0 Routing

- BGP Peers: 640
- Prefix-lists: 500
- Prefix-list entries: 10
- Logical Routers: 160
- Subtending Tier-1 Logical Routers: 400

## Tier-1 Routing

- Logical Routers: 4,000
- Gateways per Compute Host: 1,000
- Max internal routes: 1,000
- NAT Sessions per Edge Node: 4,000,000

Desired:

- 1,500 Tier-1 Logical Routers, customers bring their own routing table
  - N-S A/P
  - NAT
  - Single Service Load Balancing

## Firewall (N-S)

- Groups: 15,000 (10 per customer)
- AD Groups, 100,000
- AD Users, 100,000
- Rules: 5,000 per Logical Router

## Firewall (Distributed)

- Logical Ports: 25,000
- Stateful Rules: 100,000
- Rules Per Compute Host: 10,000

## Load Balancing

- Small Load Balancer per M Node: 10
- Small Load Balancer per L Node: 40
- Small Load Balancer per XL Node: 80
- Small Load Balancer per BM Edge Node: 750
- vIPs per Small Load Balancer: 20

## VPN

- IPSec L2L:
  - Small: 128
  - Medium: 256
  - Large: 512
  - XL: 512
  - BM: 512

## Service Insertion (N-S)

- Services: 4
- SVMs: 200
- Rules: 10,000

## Service Insertion (Distributed)

- Logical Ports: 10,000
- Hosts with active Network Introspection: 256
- Service Insertion Policies per Compute Host: 100
- Services: 8
- Chains: 24
- SVMs: 72
- Redirection Rules: 10,000

## Guest Introspection:

- App VMs per Compute Host: 40
- VMs per Compute Host: 256
- VMs: 7,500

## D-IDS

Not really viable here.

- Compute Hosts: 256
