# Case study: Operating a small Linux fleet with NixOS

**Project:** [repparw/nix](https://github.com/repparw/nix)  
**Type:** Personal infrastructure and open-source configuration, not commercial production experience.

## Problem and scope

I maintain three Linux hosts with different hardware and responsibilities: `alpha` (workstation and services), `pi` (Raspberry Pi 5 home server and deployment controller), and `epsilon` (aarch64 VPS and public-facing services). Manual changes across these machines make it harder to reproduce systems, understand failures, and recover after an incident.

## Approach

- Manage host configuration through [NixOS flakes, Home Manager, and reusable modules](https://github.com/repparw/nix#what-this-demonstrates).
- Use [deploy-rs and a Pi-based deployment controller](https://github.com/repparw/nix/blob/main/docs/runbooks/fleet-operations.md#controller-deployment-and-recovery). The controller checks CI for the revision, prepares hosts, performs health checks, and retains rollback paths. An active workstation session can defer that host.
- Collect metrics and filtered journals with Alloy into [Grafana Cloud](https://github.com/repparw/nix/blob/main/docs/runbooks/monitoring.md). Keep Cloud availability separate from deployment health so a monitoring outage does not itself block recovery.
- Use Restic and service-specific exports for [offsite backups](https://github.com/repparw/nix/blob/main/docs/runbooks/fleet-operations.md#offsite-backup-coverage-and-consistency). Report incomplete exports separately from successful uploads.
- Keep credentials in SOPS and document [recovery operations](https://github.com/repparw/nix/blob/main/docs/runbooks/host-recovery.md).

## Engineering decisions

- **Reproducibility:** A Git revision represents the desired configuration; the deployed revision is tracked separately until every selected host has been verified.
- **Failure evidence:** Failed scheduled jobs retain their status until a successful rerun. Clearing a systemd failure flag is not treated as proof of recovery.
- **Recovery before cleanup:** Deployment rollback roots and backup consistency checks are preserved rather than assuming a green CI check or successful upload guarantees a working restore.

## What this demonstrates

Linux administration, deployment automation, service troubleshooting, networking, observability, backup design, and operational documentation. The environment is small, but the work is inspectable through its configuration, tests, and runbooks.

**Evidence:** [Repository overview](https://github.com/repparw/nix) · [Fleet operations](https://github.com/repparw/nix/blob/main/docs/runbooks/fleet-operations.md) · [Monitoring](https://github.com/repparw/nix/blob/main/docs/runbooks/monitoring.md) · [Restore procedures](https://github.com/repparw/nix/blob/main/docs/runbooks/restore-service-backups.md)
