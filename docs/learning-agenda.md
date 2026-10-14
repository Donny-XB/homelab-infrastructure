# Learning Agenda

This roadmap prioritizes practical, fun projects while building deeper infrastructure, automation, security, RF, and AI skills.

## Current Project Sequence (updated 2026-10-14)

1. **Completed milestone:** Raspberry Pi 5 NAS with OpenMediaVault 8, SMB shares, Docker and remotely accessible Plex. See [build log](build-log-2026-10-14-nas-plex.md).
2. **Next priority:** Run a fully local AI assistant on the Dell OptiPlex 7060 to tutor cybersecurity concepts and prepare authorized future lab exercises. Choose the runtime/model after inspecting the Dell's actual hardware. Set up only the virtualization/platform infrastructure the AI needs.
3. **After local AI works:** Build isolated cybersecurity VMs and begin blue-team, red-team, and purple-team studies, including the planned wireless/RF topics.
4. **As resources permit:** Acquire an independent backup drive, verify restores, and revisit email alerts. Other automation, privacy, self-hosting and hardware projects remain on the roadmap but do not block the local AI milestone.

The phases below are **topic buckets**, not strict chronological prerequisites; the current sequence above takes precedence.

## Phase 1 — Core Home Infrastructure

- Install and learn Proxmox VE on the Dell OptiPlex 7060
- Build the Raspberry Pi NAS
- Configure storage, SMB/NFS shares, permissions, and backups
- Connect Proxmox services to NAS storage
- Deploy Jellyfin and Immich
- Learn basic Linux administration, networking, Docker, and service management

## Phase 2 — Home Automation and Physical Security

- Deploy Home Assistant
- Integrate Ring cameras and events
- Build dashboards and useful automations
- Add ESP32-based sensors
- Build a smart room-door access system using NFC/RFID and/or PIN
- Add logging, access history, local control, and mechanical fail-safe access
- Learn BLE, NFC, RFID, relays, GPIO, and basic embedded systems

## Phase 3 — Python and Automation

- Learn Python through practical homelab tools
- Build NAS health checks
- Build backup-verification scripts
- Build network inventory tooling
- Build log parsers and event correlation
- Automate Home Assistant and infrastructure APIs
- Version projects and documentation in GitHub

## Phase 4 — Privacy and Self-Hosting

- Build a personal privacy-audit workflow
- Track exposed personal information and removal requests
- Learn encryption, secrets management, MFA, and password-vault concepts
- Add DNS filtering with Pi-hole or AdGuard Home
- Build an offline knowledge server
- Practice backup and disaster recovery

## Phase 5 — Local AI and Agents (moved forward as immediate next project)

- First deliver a private, offline-capable cybersecurity tutoring assistant before pursuing lab attack/detection training.
- Keep inference off the Raspberry Pi NAS when possible; prefer the Dell OptiPlex 7060 after checking hardware resources.

- Run a local LLM where practical
- Build a read-only homelab status agent
- Add infrastructure, media, privacy, recovery, and security-analysis agents
- Use narrowly scoped tools instead of unrestricted shell/root access
- Require approval for destructive or privileged actions
- Log agent actions and permissions

## Phase 6 — Blue Team

- Deploy Sysmon on Windows lab systems
- Deploy Wazuh or another SIEM
- Learn Suricata, Zeek, and Wireshark
- Centralize Windows, Linux, firewall, and network telemetry
- Build dashboards and alerts
- Investigate simulated incidents
- Write detection rules
- Map detections to MITRE ATT&CK
- Practice incident response and recovery

## Phase 7 — Red Team and Purple Team

- Build an isolated security range
- Use Kali Linux and intentionally vulnerable targets
- Learn reconnaissance, enumeration, web security, privilege escalation, and Active Directory attack paths
- Use attack simulations only on systems owned or explicitly authorized for testing
- After each attack, switch to blue-team analysis
- Capture telemetry, build detections, harden the environment, and retest
- Document the full attack → detect → improve cycle

## Phase 8 — SDR and RF Fundamentals

- Start with an RTL-SDR receiver
- Learn spectrum visualization and frequency bands
- Learn antennas, gain, polarization, bandwidth, and path loss
- Learn modulation basics: AM, FM, FSK, PSK, QAM, OFDM
- Learn SNR/SINR, filtering, and receiver selectivity
- Explore ADS-B, weather radio, amateur-radio signals, and other legal passive reception
- Build an SDR station and logging workflow

## Phase 9 — Weather Satellite Receiver

- Learn satellite passes, orbital tracking, Doppler shift, and antenna orientation
- Build a receive-only weather-satellite station
- Capture satellite transmissions legally
- Decode weather imagery
- Automate pass prediction, recording, decoding, and archiving
- Feed decoded products into the homelab dashboard

## Phase 10 — Surveillance Technology Awareness

- Learn visual identification of common surveillance hardware
- Study ALPR/LPR, PoE cameras, LTE-connected cameras, IR illumination, and IoT camera architecture
- Use public transparency sources and lawful passive observation
- Learn passive RF surveying and why attribution is difficult
- Build a local database/dashboard of confirmed observations
- Explore computer vision for identifying equipment from your own images

## Phase 11 — Controlled RF Interference Lab

Goal: understand interference and anti-jam concepts without radiating harmful interference.

- Study noise, tones, sweep interference, narrowband vs wideband interference, and link budgets
- Learn how interference affects SNR/SINR and receiver performance
- Build a conducted RF test bench using coax, attenuators, splitters, dummy loads, and/or shielded enclosures
- Generate test signals and controlled interference entirely inside the contained setup
- Measure signal degradation and recovery
- Learn anti-interference techniques: filtering, coding, spread spectrum, frequency hopping concepts, and directional antennas

## Phase 12 — RF Red Team / Blue Team

### RF Red Team
- Characterize a test receiver and its failure points inside the contained lab
- Create controlled interference scenarios
- Test resilience of systems you own
- Explore protocol behavior under degraded RF conditions
- Document assumptions, attack surface, and observed failure modes

### RF Blue Team
- Detect interference and abnormal spectrum conditions
- Establish normal RF baselines
- Build spectrum-monitoring alerts
- Measure occupancy, noise floor, and signal strength changes
- Practice direction-finding concepts with legal test transmitters
- Test filtering, antenna placement, shielding, and other mitigations
- Compare before/after measurements

### Purple Team Loop
1. Establish baseline
2. Introduce controlled impairment
3. Detect and characterize it
4. Apply mitigation
5. Repeat the test
6. Document the result

## Phase 13 — Advanced Hardware and Wireless Projects

- Build a cyberdeck
- Add Proxmark/Flipper experiments with hardware you own
- Explore BLE and RFID security
- Build a firmware/hardware-hacking bench
- Learn UART, SPI, I2C, JTAG, and flash-memory basics
- Inspect and reverse-engineer firmware from owned test devices
- Add HackRF-class hardware only after RF fundamentals are solid

## Phase 14 — Mission Control

- Build a single dashboard for:
  - Proxmox
  - NAS health
  - Jellyfin/Immich
  - Home Assistant
  - Ring/local cameras
  - smart access
  - network health
  - security alerts
  - SDR/weather-satellite status
  - RF monitoring
  - backups
  - AI-agent summaries

## Guiding Principle

Build something interesting, understand how it works, secure it, break it safely, observe what happened, improve it, and document the process.
