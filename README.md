# Ulises Britos

**Linux systems · Infrastructure automation · Troubleshooting**

I build and operate Linux-based infrastructure, automate repetitive work, and investigate failures across systems, networks, and services. My hands-on experience comes primarily from maintaining a personal NixOS fleet and contributing to open-source projects. I use version control, CI, monitoring, and operational documentation to make changes traceable and recoverable.

Based in Argentina. **Open to remote roles** in Linux infrastructure, system administration, DevOps, and technical support.

**[Technical evidence for support and infrastructure roles](projects/technical-evidence.md)**: three short, source-backed cases covering a Linux service failure, monitoring and recovery, and a stateful API integration.

## Selected work

### [NixOS infrastructure](https://github.com/repparw/nix)

Declarative configuration and operations for a three-host fleet: a workstation, Raspberry Pi 5, and aarch64 VPS.

- NixOS flakes, Home Manager, reusable modules, and deploy-rs for deployments.
- systemd services and containers, HTTPS ingress, Authelia SSO, and SOPS-managed secrets.
- Grafana Cloud monitoring, Restic backups, CI checks, and documented recovery procedures.

[Architecture and runbooks](https://github.com/repparw/nix/tree/main/docs) · [Technical case study](projects/nixos-fleet.md)

### [Terraform / OpenTofu provider for TP-Link](https://github.com/repparw/terraform-provider-tplink)

Python/Pyvider provider for an Archer AX23 v2.0, verified on hardware. It manages DHCP reservations and port-forwarding rules.

- Supports import, drift detection, resource replacement, and verification after writes.
- Includes optional RSA authentication-key pinning and a read-only inventory tool.
- Uses unit and Terraform lifecycle tests, with frozen builds for Linux, macOS, and Windows.

**Status:** [v0.1.0 is available on GitHub](https://github.com/repparw/terraform-provider-tplink/releases/tag/v0.1.0). v0.1.0 is listed in the [Terraform Registry](https://registry.terraform.io/providers/repparw/tplink/latest) and [OpenTofu Registry](https://search.opentofu.org/provider/repparw/tplink/latest).

[Implementation and tests](https://github.com/repparw/terraform-provider-tplink/tree/main/python) · [Technical case study](projects/tplink-provider.md)

### [Grafana Cloud monitoring](https://github.com/repparw/grafana)

Version-controlled dashboards and operational documentation for Linux fleet monitoring, alerts, and configuration backups. Dashboard changes use Git Sync and pull requests; full restore verification remains pending.

[Dashboards and runbooks](https://github.com/repparw/grafana)

## Open-source work

I contribute fixes, testing, and reviews to projects involving Linux packaging, developer tools, and game streaming. [Browse my pull requests](https://github.com/search?q=is%3Apr+author%3Arepparw&type=pullrequests).

## Tools and technologies

**Systems:** Linux, NixOS, systemd, containers, DNS, HTTP/TLS, networking, SSO  
**Automation and development:** Python, Bash, Nix, Terraform/OpenTofu, GitHub Actions  
**Operations:** Grafana, Prometheus-compatible metrics, Restic, SOPS, CI/CD, troubleshooting

I'm interested in remote teams that need someone who can automate routine work, investigate problems, and document reliable fixes.

[LinkedIn](https://www.linkedin.com/in/ubritos/) · [GitHub](https://github.com/repparw)
