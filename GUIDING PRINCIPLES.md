# Guiding Principles

## Multi-Tenancy

- ~400 IaaS consumers
- ~40 IaaS consumers w/ dedicated hardware

## Standard Tenant Sizing

- ~10 VMs per customer
- Typically DaaS or 3-tier Web Apps

## Dedicated Tenants

- Can run own TZ, NSX-T Manager to reduce overhead on shared resoureces

## Administrative Multi-Tenancy

- Given that the customer tenant count exceeds reference scale for NSX-T RBAC, self-service is infeasible by direct appliance access. Fortunately, the customer already is using vCloud Director for this purpose, and their customers are already familiar with the platform. All customer administrative changes *SHOULD* go through vCD, wherever possible.

## Shared Services Tenant

- Must interconnect to all ~430 customers with potentially overlapped addressing

## Dataplane Multi-Tenancy

## Bridging

- Do not bridge between network kinds wherever feasible, and constrain solutions doing so to their specific need or use case

## IPv6

- IPv6 should be used or usable wherever possible
