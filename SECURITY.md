# Cloud Service Provider Security Model

To provide scalable, cost-effective infrastructure, the "Service Provider" Zilungele Cloud Services must provide a clear-cut outline indicating where security responsibilities exist.

## Service Provider Responsibilities

The "Service Provider" *WILL* retail ultimate responsibility for the security of:

- Cloud Management Platforms, e.g. `vCloud Director Cells`
- IaaS Components, e.g. `VMware Cloud Provider Pod` or `VMware Cloud Foundations`
- Identity and Access Management for CMP/IaaS
- Hypervisors and Bare Metal Compute
- Storage Platforms
- Physical Facilities
- Inter-Availability Zone Backbone Networks
- Inter-Region Availability Zone Backbone Networks
- Tenant Network Separation
- Regional facilities and Availability Zones

## Customer Responsibilities

The "Customer" *WILL* retail ultimate responsibility for the security of:

- Application Security
- Placement of workloads to best achieve Availability goals
- Guest Operating System Security
- Confidentiality for Data stored in ZCS
- Confidentiality for Data in transit
- Network Security within the Tenant network, and any interconnection thereof
- Identity and Access Management within the Tenant
