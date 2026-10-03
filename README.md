# Home Lab Infrastructure

A living portfolio documenting the design, deployment, security, automation, and recovery of my self-hosted home infrastructure.

## Current Goals

- Build a Proxmox virtualization host on a Dell OptiPlex 7060 Micro
- Build a Raspberry Pi-based NAS for centralized storage and backups
- Self-host media and photo services
- Integrate Home Assistant and Ring
- Develop Python automation and monitoring tools
- Explore local AI for infrastructure operations
- Improve privacy, backup, and recovery practices
- Later build an isolated red-team / blue-team security lab

## Planned Architecture

- **Compute:** Dell OptiPlex 7060 Micro running Proxmox VE
- **Storage:** Raspberry Pi 5 NAS with powered multi-bay SATA enclosure
- **Automation:** Home Assistant
- **Media:** Jellyfin
- **Photos:** Immich
- **Development:** Python, Git, APIs
- **AI:** Local LLM tooling
- **Security:** Network segmentation, logging, monitoring, lab attack/detection exercises

## Repository Structure

- `docs/` — architecture diagrams, build logs, and security notes
- `proxmox/` — virtualization configuration and notes
- `nas/` — storage, shares, backup and recovery
- `home-assistant/` — automations and integrations
- `self-hosting/` — Jellyfin, Immich, Docker and related services
- `python/` — automation, monitoring, and tooling
- `ai/` — local AI experiments and integrations
- `privacy/` — sanitized privacy and data-protection workflows
- `security-lab/` — isolated red-team / blue-team exercises

## Security Note

This repository must not contain passwords, API keys, tokens, public IP addresses, private home addresses, Ring credentials, Wi-Fi credentials, or other sensitive network details.

## Status

**Phase 1:** Hardware acquisition and Proxmox setup.
