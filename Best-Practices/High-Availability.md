# High-Availability

# Profisee High Availability

---

Profisee High Availability (HA) ensures continuity of master data management operations by distributing core services and workloads across multiple nodes. When HA is enabled, requests can be processed by any Profisee node. When implemented behind a load balancer, HA provides resiliency for supported services, minimizing downtime for mission-critical use cases.

**Key benefits:** Redundancy for core services, load distribution across multiple nodes, and compatibility with standard enterprise infrastructure patterns.

---

## Supported Deployment Architectures

The following table summarizes the deployment models supported for HA and their key requirements.

| **Architecture** | **Supported** | **Requirements & Notes** |
| --- | --- | --- |
| **PaaS Container** | ✓ Yes | Azure-hosted container deployment. No limit to number of nodes. Primary tested and recommended architecture. |
| **SaaS Container** | ✓ Yes | Managed by Profisee. Three nodes running in separate node pools distributed across three availability zones. Primary tested and recommended architecture. |
| **Installed On-Prem (VM)** | ✓ Yes | No limit to number of nodes. Server or VM must be Active Directory / domain-joined. Non-domain-joined environments are not supported. |
| **Installed Azure VM** | ✓ Yes | No limit to number of nodes. Azure VM must be AD / domain-joined. Use native Azure networking and load balancing. |

> [!NOTE]
> Note: Profisee formally tests and supports Azure and on-premises deployments. Additional cloud platforms may be supported in future based on customer demand.

---

## Service Failover Behavior

Not all Profisee services support a distributed architecture. The sections below clarify which services are distributed and support HA, and which require manual intervention or are excluded.

### Distributed Services

These services are distributed across nodes. Load balancers can redirect traffic to healthy nodes if one becomes unhealthy.

| **Service** | **Details** |
| --- | --- |
| **Modeling** | Creation and modification of the data model, including entities, attributes, and relationships. |
| **Data Operations** | All record-level operations: creates, updates, and deletes. |
| **Authentication** | The ability for users to authenticate and log in. |
| **FastApp Portal** | The FastApp Portal, including the Data Browser, FastApp, Form, and Presentation View administration. |
| **Task Management** | Coordination of stewardship tasks across task originators. |
| **Script Execution** | Safe, secure sandbox for custom JavaScript actions used in Connect, Workflow, and other services. |
| **Governance** | Common governance interconnect for providers including Purview and Alation. |
| **File Attachments** | Support for unstructured data to be associated with master data content. |
| **Connect** | Integration jobs redistribute to available nodes automatically. |
| **Matching** | New matching engine workloads are balanced and recovered across nodes. |
| **Data Quality** | New rules engine processes redistribute on failover. |
| **AI Services** | AI-powered features continue operating on remaining healthy nodes. |

### Non-Distributed Services

These services are not distributed but are provided through a combination of distributed services that support HA.

| **Service** | **Details** |
| --- | --- |
| **Hierarchy Management** | The ability to define and manage hierarchies is not a distributed service. It is provided in combination by Modeling (relationships), Data Operations, and FastApps. |
| **Relationship Management** | The ability to manage relationships. |

### Node-Specific Services

These services are not implemented in a distributed architecture and are assigned to a specific node. If the node running one of these services becomes unavailable, the service will be interrupted until the node is restored or manually redirected.

| **Service** | **Details** |
| --- | --- |
| **Address Verification (Legacy)** | Legacy address verification is a single-node service and is not HA-enabled. |
| **Real Time Event Management (Eventing)** | Real Time Event Management does not work across multiple nodes. If HA is required, equivalent eventing capabilities are available in Connect, which has a distributed HA architecture. |
| **Notifications** | Notification delivery is bound to a single node. This will be addressed in 2026 as part of the transition to a new workflow architecture. |
| **Workflow** | Workflow execution may behave unpredictably in multi-node configurations. This will be addressed during 2026 as Profisee transitions to a new workflow engine architecture. |
| **Staging** | If HA is required, most Staging capabilities are available in Connect, which supports an HA architecture. Staging is only available to IaaS (on-prem) and PaaS customers. |

---

## Configuration Guidance

### General Approach

1. Configure load balancing and networking per your architecture (primary node only).
2. Deploy and fully configure your first (primary) Profisee node.
3. Verify the single-node deployment is fully operational.
4. Add additional nodes to the deployment.
   * For self-managed customers, there is no limit to the number of nodes.
   * For SaaS customers, HA includes three nodes across three separate node pools running across three availability zones.
5. Configure load balancing and networking to point to all nodes.

### Networking & Load Balancing

* **Sticky sessions** are required for SignalR connections. Configure your load balancer to use session affinity for real-time UI operations.
* For **Azure VM deployments**, use Azure Load Balancer or Application Gateway with standard Azure networking.
* For **on-premises deployments**, use your existing enterprise load balancer with health-check probes directed at the Profisee application tier.
* Ensure required ports are open between all nodes and the shared database tier. Contact Profisee Support for the full port reference.

### Domain Requirements

For installed (non-container) deployments, all servers and VMs participating in the HA cluster must be joined to an Active Directory domain. Non-domain-joined machines are not currently supported.

---

## Licensing

Profisee HA is licensed as a single add-on option rather than by individual node count. This simplifies procurement and scales with your deployment needs.

| **License Type** | **HA Licensing** |
| --- | --- |
| **Subscription / SaaS** | Add the HA option to your existing subscription. Covers up to three nodes. |
| **Perpetual** | HA is available as an add-on. Contact your Profisee account representative for pricing details. |

For licensing inquiries or to enable HA on your account, contact your Profisee account representative or reach out to [sales@profisee.com](mailto:sales@profisee.com).

---