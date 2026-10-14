# Build Log — 2026-10-14: Raspberry Pi 5 NAS and Plex

**Milestone:** First functional self-hosted NAS and media service  
**Status:** Core setup operational; maintenance and backups remain ongoing work.

## Hardware and system
- Raspberry Pi 5 running 64-bit Raspberry Pi OS Lite on Debian 13 (Trixie).
- Seagate IronWolf 4 TB drive attached via a USB enclosure.
- OpenMediaVault 8 installed as the storage management platform.
- Headless SSH administration over Ethernet; system packages updated.

## Storage and file sharing
- Prepared and mounted the IronWolf with an EXT4 filesystem.
- Configured Samba/SMB authenticated shares:
  - **NAS** — primary Windows-mapped network drive, containing **Media**, **Docs**, and **Backups** as subfolders.
  - **CyberLabs** — separate share intended for future security projects and tighter access controls.
- Created and verified a non-administrative SMB user, kept distinct from the SSH and OMV administrative accounts.
- Resolved old Windows SMB credential conflicts after an account rename.
- Configured a DHCP reservation to keep the NAS's local IP stable.
- Enabled SMART health monitoring and scheduled short and extended drive self-tests.

## Docker and Plex
- Installed the OpenMediaVault Compose plugin and Docker Engine.
- Moved Docker storage to the IronWolf instead of relying on the Pi's microSD card.
- Deployed Plex Media Server in a Docker container with persistent application data.
- Mapped the NAS Media directory into Plex as **read-only**.
- Verified local Plex playback.
- Configured a single manually forwarded TCP port for Plex on the Verizon router.
- Troubleshot remote access, including identifying how a Windows VPN caused a misleading public-IP port test.
- Confirmed **remote Plex playback works** from outside the home network.

## Concepts practiced
Linux administration and shell commands; SSH; ARM64 and Debian version compatibility; filesystems; users, groups, and permissions; SMB shares vs directories vs mapped drives; DHCP reservation; SMART monitoring; Docker containers and persistent volumes; NAT and port forwarding; local vs remote connectivity troubleshooting.

## Outstanding work and cautions
- No second backup device is available yet. The **Backups** folder is only a folder on the same disk, not independent protection against IronWolf failure. Backup configuration is deferred until another drive is acquired.
- Email notifications were intentionally deferred.
- Full migration of the old Windows Plex library and decommissioning its server are **not yet verified**.
- Keep Plex and its container image patched because the media service is reachable remotely. Do not expose SMB, SSH, or the OMV admin UI to the internet.
- The USB enclosure's long-term SMART reporting and backup/restore procedures should be periodically verified.

## Next major project (priority changed today)
**Build a fully local, self-hosted AI assistant before beginning the cybersecurity lab curriculum.**

- Preferred compute host: Dell OptiPlex 7060; leave the Raspberry Pi focused on NAS/Plex.
- Inspect the Dell's actual CPU, RAM, storage, and available GPU capabilities before choosing the AI runtime or model.
- Prioritize an offline-capable **cybersecurity tutor** that explains concepts, helps plan authorized lab exercises, quizzes understanding, and references personal notes.
- Use local data storage, narrowly scoped permissions, and no automatic privileged or destructive actions.
- After local AI is functional, proceed into Proxmox/VMs as needed and isolated blue-team, red-team, and purple-team labs.

## Personal reflection
Today moved the homelab from parts and plans into an always-on service. I assembled a working Linux NAS, made storage available across my home network, learned the practical difference between local and remote connectivity, and got my Plex library service operating without depending on my everyday Windows computer. The work involved mistakes, diagnosis, and iteration—not just following commands. The next step is a local AI tutor, but the right move now is to take a break.
