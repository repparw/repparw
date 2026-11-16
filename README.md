# Ulises Britos

**Linux systems · Infrastructure automation · Troubleshooting**

I build and run Linux infrastructure, automate repetitive work, and troubleshoot systems, networks, and services. Most of my hands-on experience comes from running my own NixOS fleet and contributing fixes to open-source projects.

**Looking for remote work** in Linux infrastructure, DevOps and automation, IT operations, implementation, or technical support. Based in Argentina.

[Résumé](https://cv.repparw.com/) · [LinkedIn](https://www.linkedin.com/in/ubritos/)

**[Technical examples](projects/technical-evidence.md):** three short cases, each linked to its source: a Linux service failure, monitoring and recovery, and a stateful API integration.

## Selected work

### [NixOS infrastructure](https://github.com/repparw/nix)

Declarative configuration for three hosts: a workstation, a Raspberry Pi 5, and an aarch64 VPS.

- Built with NixOS flakes, Home Manager, reusable modules, and deploy-rs.
- Runs systemd services and containers behind HTTPS, with Authelia SSO and SOPS-managed secrets.
- Monitored with Grafana Cloud, backed up with Restic, checked by CI, and covered by written recovery procedures.

[Architecture and runbooks](https://github.com/repparw/nix/tree/main/docs) · [Case study](projects/nixos-fleet.md)

### [Terraform / OpenTofu provider for TP-Link](https://github.com/repparw/terraform-provider-tplink)

A Python (Pyvider) provider that manages DHCP reservations and port-forwarding rules on an Archer AX23 v2.0. Tested on real hardware.

- Supports import, drift detection, resource replacement, and checks after writes.
- Optional RSA authentication-key pinning, plus a read-only inventory tool.
- Unit tests and Terraform lifecycle tests, with standalone builds for Linux, macOS, and Windows.

**Status:** v0.1.0 is [released on GitHub](https://github.com/repparw/terraform-provider-tplink/releases/tag/v0.1.0) and listed in the [Terraform Registry](https://registry.terraform.io/providers/repparw/tplink/latest) and [OpenTofu Registry](https://search.opentofu.org/provider/repparw/tplink/latest).

[Implementation and tests](https://github.com/repparw/terraform-provider-tplink/tree/main/python) · [Case study](projects/tplink-provider.md)

### [Grafana Cloud monitoring](https://github.com/repparw/grafana)

Version-controlled dashboards and runbooks for fleet monitoring, alerts, and configuration backups. Dashboard changes go through Git Sync and pull requests. I haven't tested a full restore yet.

[Dashboards and runbooks](https://github.com/repparw/grafana)

## Open-source work

I contribute fixes, testing, and reviews to projects in Linux packaging, developer tools, and game streaming. [See my pull requests](https://github.com/search?q=is%3Apr+author%3Arepparw&type=pullrequests).

## Skills

- **Systems:** Linux, NixOS, systemd, containers, DNS, HTTP/TLS, networking, SSO
- **Automation and development:** Python, Bash, Nix, Terraform/OpenTofu, GitHub Actions
- **Operations:** Grafana, Prometheus-compatible metrics, Restic, SOPS, CI/CD, troubleshooting
