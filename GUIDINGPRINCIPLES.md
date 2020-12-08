# Guiding Principles

## Multi-Tenancy

- ~400 IaaS consumers, 2 year projection of ~800
- ~40 IaaS consumers w/ dedicated hardware, 2 year projection of ~80
- ~1500 projected tenant scale per CIO

## Standard Tenant Sizing

- ~10 VMs per customer
- Typically DaaS or 3-tier Web Apps
- ~4 `vn-segments` per customer
- Probably high 80/20 N/S
- Dedicated IPs per tenant - for IPsec L2L, and public services?

## Dedicated Tenants

- Can run own TZ, NSX-T Manager to reduce overhead on shared resoureces
- Customers probably will not balk at costs for dedicated platform, as they're already paying it. Management WLD may require additional consideration.

## Administrative Multi-Tenancy

- Given that the customer tenant count exceeds reference scale for NSX-T RBAC, self-service is infeasible by direct appliance access. Fortunately, the customer already is using vCloud Director for this purpose, and their customers are already familiar with the platform. All customer administrative changes *SHOULD* go through vCD, wherever possible.

## Shared Services Tenant

- Must interconnect to all ~430 customers with potentially overlapped addressing. Given that this number already exceeds scalability limits, a more "cloud-like" approach may be necessary here, like IPSec on A/P T0 in a shared service deployment (on a separate manager)
- Probably needs public netblocks. See note about IPv6

## Dataplane Multi-Tenancy

## Availability Zones

- Customer already has 2 AZs per region (*city*)
- Each Availability zone will have A/A redundant components, including a shared services pod and network egress.

## Public Cloud on-Ramp

- Route-based L2L IPSec is an already established standard. *Nick* this may be feasible for infrastructure tenant universal access a la' transit gateways

## Uptime SLA

- 99.99%

## Scale

- 6,000 `vn-segments`
- 1,500 `logical routers`
- Lots and lots of bulk crypto for the IPSec on/off ramp

## Bridging

- Do not bridge between network kinds wherever feasible, and constrain solutions doing so to their specific need or use case

## IPv6

- IPv6 should be used or usable wherever possible
