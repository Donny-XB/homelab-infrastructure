# Home Lab Infrastructure

A living portfolio documenting the design, deployment, security, automation, and recovery of my self-hosted home infrastructure.

## Current Status — 2026-10-14

**Milestone reached: Raspberry Pi NAS and Plex are operational.**

- Raspberry Pi 5 with Raspberry Pi OS Lite / Debian 13 and OpenMediaVault 8.
- Seagate IronWolf 4 TB EXT4 storage.
- Two authenticated SMB shares: **NAS** (Media, Docs, Backups) and **CyberLabs** (separate).
- NAS mapped as a Windows network drive; router DHCP reservation configured.
- SMART monitoring and scheduled disk health tests enabled.
- Docker and Compose installed, with container data on the HDD.
- **Plex Media Server** deployed in Docker; local and remote streaming tested successfully.
- Backup to an independent second device **not yet configured**; email alerts deferred.

Detailed work log: [October 14 NAS and Plex milestone](docs/build-log-2026-10-14-nas-plex.md).

## Immediate Next Priority

**Build a fully local AI assistant/tutor before starting the cybersecurity labs.**

The preferred AI host is the Dell OptiPlex 7060 rather than the Raspberry Pi, which will continue serving NAS and Plex workloads. Select the local model and runtime only after verifying the Dell's CPU, RAM, GPU, and storage. Focus first on cybersecurity tutoring, study support, safe lab guidance, and local reference notes. Keep tool permissions narrow and require approval for system-changing actions.

After the AI assistant is usable, proceed to the isolated blue-team/red-team/purple-team learning environments.

## Complete Learning Curriculum

The [**expanded Techie learning curriculum**](docs/learning-agenda.md) includes **17 hands-on tracks (0–16)**, each with learning objectives, exercises, practical deliverables, and progress checkpoints. **Learning depth and just-in-time language sequencing updated October 25, 2026.**

- **Foundation and immediate next:** Completed Pi-NAS/Plex build, **fully local AI cybersecurity tutor on the Dell**, Linux/networking/virtualization, Python and automation.
- **Cybersecurity:** Blue-team monitoring and incident response; isolated red-team and purple-team exercises; dedicated **Pwnagotchi/Wi-Fi security** (authorized capture auditing, Kismet/Wireshark, Python plugins, wireless defense). See the [12 advanced Red/Blue/Purple Team modules and investigation capstone](docs/red-blue-purple-specializations.md): threat hunting, adversary emulation, detection engineering, DFIR, malware research, AD/identity, web/API, cloud, deception, CTI, DevSecOps and BAS.
- **Self-hosting and physical technology:** Privacy, backups, home automation/Ring, smart access, IoT and local AI agents.
- **RF and hardware:** SDR fundamentals, weather satellite reception, surveillance/ALPR technical awareness, strictly contained RF interference/resilience labs, RF red/blue/purple tests, cyberdeck/Flipper/Proxmark/embedded firmware, and a future mission-control dashboard.

**Personalized learning depth:** **Go deep** on network security/reconnaissance, threat hunting/DFIR, Red Team/penetration testing, malware analysis/reversing (later), web/API security, OSINT/CTI, and AI security. **Working knowledge** in RF/SDR/wireless and embedded/hardware. **Just explore** cloud security. Learn each supporting language only when a real project requires it: Python first, JS/PHP/SQL with web work, PowerShell for Windows, and C/C++/Assembly later with malware analysis. See the [master learning-depth matrix](docs/learning-agenda.md#personalized-cybersecurity-learning-depths-updated-2026-10-25) and [advanced specialization guide](docs/red-blue-purple-specializations.md).

The topics are an interest-driven playground rather than a fixed study timetable. **Local AI and properly isolated lab infrastructure precede risky cybersecurity exercises**, and independent NAS backup remains deferred until a separate physical drive is available.

## Cybersecurity Hardware & Field Toolkit

The [**Cybersecurity Hardware & Tooling Curriculum**](docs/cybersecurity-hardware-toolkit.md) covers **Flipper Zero, Proxmark3, Pwnagotchi, WiFi Pineapple, HackRF, RTL-SDR, Wi-Fi monitoring, USB Rubber Ducky, O.MG Cable, LAN Turtle, Bus Pirate, JTAG/firmware tooling, ESP32 and cyberdecks**. It maps each optional tool to protocol fundamentals, authorized hands-on labs, Blue/Red/Purple exercises, and documented checkpoints. Hardware learning follows the local AI milestone and is **not** an equipment purchase commitment.

## Additional Goals

- Prepare the Dell OptiPlex for virtualization and lab VMs (Proxmox VE if suitable).
- Add a **separate backup destination** and practice restore/recovery.
- Integrate Home Assistant and Ring, add personal automations and monitoring.
- Develop Python automation and infrastructure tools.
- Explore photo management (Immich), optional alternative media stacks, and privacy/self-hosting.
- Expand into RF/SDR and authorized wireless security labs when foundational work is ready.

## Architecture

- **Storage and media:** Raspberry Pi 5 NAS, OpenMediaVault 8, IronWolf 4 TB, Docker, Plex.
- **Next compute:** Dell OptiPlex 7060 for local AI; eventual virtualization and cybersecurity labs.
- **Automation (planned):** Home Assistant and narrowly scoped agent integrations.
- **Development:** Python, Git, APIs.
- **Security (planned):** Segmented lab networks, logging, monitoring, safe attack/detection exercises.

## Repository Structure

- `docs/` — architecture notes, learning agenda, and dated build logs
- `proxmox/` — virtualization configuration and notes (planned)
- `nas/` — storage, shares, backup and recovery (planned)
- `home-assistant/` — automations and integrations (planned)
- `self-hosting/` — Plex and other services (planned)
- `python/` — automation, monitoring, and tooling (planned)
- `ai/` — local AI experiments and integrations
- `privacy/` — sanitized privacy and data-protection workflows (planned)
- `security-lab/` — isolated red-team / blue-team exercises (planned)

## Security Note

Do not commit passwords, API keys, tokens, public IP addresses, private home addresses, MAC addresses, Wi-Fi credentials, Ring credentials, or sensitive network details to this repository. Describe configurations without sharing secrets.

## Build Log

- [2026-10-14 — Raspberry Pi NAS and Plex](docs/build-log-2026-10-14-nas-plex.md)
