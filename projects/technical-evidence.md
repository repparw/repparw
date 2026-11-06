# Technical evidence for support and infrastructure roles

I maintain personal Linux infrastructure and contribute to open-source projects. The examples below show inspectable troubleshooting, operations, and software-integration work. They are **not examples of paid customer support or commercial production service ownership**.

## 1. Diagnosing a service lifecycle failure

**Problem:** Active game-streaming sessions could be interrupted when a systemd daemon reload produced a unit-removal event.

**Investigation and fix:** Followed the service-event handling path and distinguished a temporary `UnitRemoved` signal from a genuinely stopped service. The change queries the current unit state before handling the event as termination.

**Evidence:** [Merged Moonshine PR #231](https://github.com/hgaiser/moonshine/pull/231).

**Relevant to:** Linux support, issue reproduction, logs and state analysis, safe bug fixes, and communication through code review.

## 2. Monitoring and restoring Linux services

**Problem:** A small fleet spanning a workstation, Raspberry Pi server, and cloud VPS needed repeatable deployment checks and enough observability to distinguish service faults from monitoring faults.

**Approach:** Configured system services, centralized metrics and logs through Alloy/Prometheus-compatible ingestion and Loki/Grafana, and documented deployment, health-check and recovery procedures. During a controlled interruption, validated authenticated ingestion and subsequent recovery; did not treat a successful upload as proof of service restoration.

**Evidence:** [Monitoring rollout PR #281](https://github.com/repparw/nix/pull/281), [monitoring runbook](https://github.com/repparw/nix/blob/main/docs/runbooks/monitoring.md), and [fleet operations case study](nixos-fleet.md).

**Relevant to:** Monitoring alerts, incident triage, Linux administration, rollback, authentication, and technical documentation.

## 3. Working with an unreliable device API

**Problem:** A home router provides a non-transactional management interface, one active administrator session, and ambiguous outcomes if a connection times out after a write.

**Approach:** Built a Python Terraform/OpenTofu provider with import, drift detection, read-back verification, and serialized updates. Added optional RSA key pinning and tests covering normal resource lifecycles and failure conditions. The tested hardware is an Archer AX23 v2.0; support for other models is not assumed.

**Evidence:** [Provider and implementation](https://github.com/repparw/terraform-provider-tplink), [architecture notes](https://github.com/repparw/terraform-provider-tplink/blob/main/ARCHITECTURE.md), and [case study](tplink-provider.md).

**Relevant to:** API support, troubleshooting stateful integrations, Python, data validation, authentication, and careful error handling.

## Working style

These examples show how I reproduce and isolate problems, make scoped changes, verify behavior, and document limitations. I am seeking my **first professional IT position**, particularly in technical support, SaaS implementation, Linux operations, or junior infrastructure engineering.
