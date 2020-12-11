# vCloud Director

## Overview

- VMware vCloud Director allows us to convert our physical data centers into virtual data centers (VDCs). By placing network, storage and compute resources, into VDC resources, we can then make them available as catalog-based services to cusotmers through a web portal.
- VMware vCloud Director, or, if chosen, the `Zilungele Cloud Portal` is an excellent for applying limits on customers to control access and the consumption.

## Consumable Services

### Network Solutions

#### In-Scope

- IaaS Tenancy will follow the `Routed (Shared T0)` on-demand blueprint model provided natively with vCD
- Dedicated Tenancy will follow the `Routed (Dedicated T0)` on-demand blueprint model provided natively with vCD
- Shared Services hub will be natively deployed following leveraging the following service catalog items provided natively with vCD under the Provider VDC:
  - `Routed (Dedicated T0)`
  - `Shared Services vApp` *(will require some additional development with long-term benefits)*
  - This is to maximize the repeatability of the shared services hub, which *SHOULD* be implemented in every Availability Zone
- CaaS. Containers-as-a-Service will be provided, but as its own service under a standalone `Routed (Shared T0`)

#### Out-of-Scope

- External Networks.
- Desktop-as-a-Service
- Highly customised CaaS
