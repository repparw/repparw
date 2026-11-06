# Case study: Terraform/OpenTofu provider for a TP-Link router

**Project:** [repparw/terraform-provider-tplink](https://github.com/repparw/terraform-provider-tplink)  
**Status:** Hardware-verified implementation. [v0.1.0 is published on GitHub](https://github.com/repparw/terraform-provider-tplink/releases/tag/v0.1.0). v0.1.0 is listed in the [Terraform Registry](https://registry.terraform.io/providers/repparw/tplink/latest) and [OpenTofu Registry](https://search.opentofu.org/provider/repparw/tplink/latest).

## Problem and scope

My home network router needed repeatable management for DHCP reservations and port-forwarding rules. The router has a single administrative session, limited failure reporting, and no transactional multi-rule writes, so retries and uncertain write outcomes require care.

## Implementation

- Developed the active provider in Python using [Pyvider and Terraform Plugin Protocol 6](https://github.com/repparw/terraform-provider-tplink/blob/main/ARCHITECTURE.md), backed by a pinned TP-Link router client.
- Implemented two managed resources and five read-only data sources, including import, drift detection, replacement, and post-write read-back verification.
- Added optional RSA public-key pinning for router authentication and a read-only inventory command that generates Terraform import inputs.
- Automated [schema and resource lifecycle tests](https://github.com/repparw/terraform-provider-tplink/tree/main/python) with a persistent mock router, and packaged frozen executables for Linux, macOS, and Windows.
- Verified reads and complete create/update/import/destroy lifecycles against the [Archer AX23 v2.0, firmware 1.1.2 Build 20250814](https://github.com/repparw/terraform-provider-tplink#readme). Other models are not claimed as supported.

## Engineering decisions

- **Avoid duplicating protocol code:** The earlier Go implementation was retired in favor of the Python library, reducing duplicate cryptography and router-protocol maintenance.
- **Treat timeouts as uncertain:** A timeout after a write does not authorize automatic replay; the provider verifies state before assuming an operation failed.
- **Respect device constraints:** Router operations are serialized inside the provider; external users and changes can still interfere.
- **Keep distribution practical:** Frozen binaries do not require a local Python installation, with the necessary runtime caveat documented for NixOS.

## What this demonstrates

API and protocol integration, infrastructure-as-code design, test automation, hardware debugging, security checks, and careful handling of partial failures.

**Evidence:** [README and limitations](https://github.com/repparw/terraform-provider-tplink) · [Architecture decision](https://github.com/repparw/terraform-provider-tplink/blob/main/ARCHITECTURE.md) · [Implementation and tests](https://github.com/repparw/terraform-provider-tplink/tree/main/python) · [Release checklist](https://github.com/repparw/terraform-provider-tplink/blob/main/RELEASING.md)
