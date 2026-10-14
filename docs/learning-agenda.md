# Techie Homelab — Complete Learning Curriculum

**Living roadmap | Expanded 2026-10-14**  
**Philosophy:** This is a playground of hands-on projects, not a rigid productivity schedule. Follow curiosity, take breaks, and record what was learned. The suggested progression gives each experiment a useful foundation without requiring a strict calendar.

> **Current order matters:** The Raspberry Pi NAS/Plex milestone is complete. **Build the fully local AI cybersecurity tutor next.** Only then move into the cybersecurity lab exercises. Other tracks are optional branches and can be revisited freely.

## Current status and priority

| Milestone | State | Evidence / next action |
| --- | --- | --- |
| Raspberry Pi 5 NAS on Debian 13 + OpenMediaVault 8 | **Operational** | [2026-10-14 build log](build-log-2026-10-14-nas-plex.md) |
| IronWolf 4 TB EXT4 storage, authenticated SMB, mapped network drive, separate CyberLabs share | **Operational** | Local file access tested |
| SMART monitoring and scheduled disk self-tests | **Configured** | Review results periodically |
| Docker + Plex media server | **Operational** | Local and remote media playback confirmed |
| Independent NAS backup | **Deferred** | Obtain a *separate physical drive*; do **not** use the Windows PC as the substitute backup destination |
| Email alert notifications | **Deferred / optional** | Not required for current NAS operation |
| Local AI cybersecurity tutor on Dell OptiPlex 7060 | **NEXT** | Verify hardware specs, then select appropriate runtime and model |
| Cybersecurity virtual machines and lab exercises | **Planned after local AI** | Start with a contained lab network |
| Home automation, privacy, SDR/RF, satellite, hardware hacking and mission control | **Exploration tracks** | No fixed deadlines |

## Curriculum method

For each module, record four things in GitHub:
1. **Understand:** Explain the technology in your own words and draw its place in the architecture.
2. **Build:** Complete an exercise on owned hardware, authorized systems, or offline/simulated data.
3. **Observe:** Save sanitized commands/configuration, expected and actual results, failures, and fixes.
4. **Demonstrate:** Produce a working feature, repeatable test, diagram, detection, or short explanation.

**Completion labels:** Not started → Exploring → Working demo → Documented → Revisited. A working demo is useful even if it is not a full polished project. Projects can overlap.

**Documentation template:** Objective; hardware/software; prerequisites; architecture; setup steps; test cases; evidence; issues; lessons; security considerations; future improvements. Never commit secrets, personally sensitive data, actual private/public network addresses, MAC addresses, wireless capture data, or live credentials.

**Ethics and containment:** Practice offensive techniques only on systems and RF equipment owned or explicitly authorized for testing. Keep intentionally vulnerable targets isolated from personal devices and the live NAS. Do not transmit harmful RF interference or interfere with third-party wireless networks. Prefer PCAP replays, emulators, shielded setups, and sanitized datasets when possible.

---

## Track 0 — Core Home Infrastructure and NAS (working milestone)

**Purpose:** Understand how a real always-on service is built, reached, secured, maintained, and recovered.

**Topics**
- Raspberry Pi 5 hardware, power, cooling, Ethernet and headless operation.
- Raspberry Pi OS Lite, Debian releases, ARM64 compatibility, SSH, updates, services and logs.
- Storage buses and USB enclosures; GPT/partitions, EXT4, mounting, ownership, groups, ACLs and permissions.
- OpenMediaVault administration; SMB/Samba vs folders vs Windows mapped drives; separate shares and least privilege.
- IP addressing, subnet masks, ARP, DHCP reservations, DNS, mDNS, NAT, router/firewall concepts and remote-access troubleshooting.
- SMART indicators, short/extended self-tests, disk health vs actual backup.
- Docker Engine, Compose, volumes/bind mounts, persistent app data, image updates, service logs, container network modes.
- Plex as a self-hosted container: library mapping, Direct Play versus transcoding, local versus remote access, external port forwarding, risks of public services.

**Built and verified**
- Pi-NAS with IronWolf 4 TB and OMV 8.
- A main NAS SMB share (Media, Docs and Backups subfolders), and a separate CyberLabs share.
- Docker + Plex working from home and remotely.
- Windows SMB credential/identity troubleshooting, DHCP reservation and SMART testing.

**Remaining work / deliverables**
- [ ] Document restoration of OMV configuration and container data.
- [ ] Add an independent physical backup device **when obtained**; test actual restores, not just copying files.
- [ ] Review Plex patching, account security, remote exposure and eventual shutdown of the old Windows Plex server.
- [ ] Optional: NFS, UPS/power resilience, monitoring dashboards, email notifications.
- [ ] Draw a sanitized architecture diagram distinguishing NAS, router, clients, Docker and public Plex access.

**Proof of understanding:** From a different device, explain why an SMB share is not a directory, what an IP reservation does, what Docker persists, and why a single disk is not a backup.

## Track 1 — Fully Local AI Cybersecurity Tutor (**immediate next project**)

**Purpose:** Build a private assistant that teaches networking, Linux, programming, and cybersecurity, and later helps with authorized lab work.

**Architecture preference:** Keep the Raspberry Pi dedicated to NAS/Plex. Use the Dell OptiPlex 7060 as the AI compute host **after checking its actual CPU model, RAM, GPU/iGPU, storage, power limits and OS**. Do not assume a particular model size or speed in advance.

**Learning objectives**
- Understand local inference, models vs runtimes, tokens, context length, quantization, CPU vs GPU inference, memory requirements, embeddings, retrieval-augmented generation (RAG), prompt design and model limitations.
- Compare possible runtimes (e.g., llama.cpp or Ollama) and local chat interfaces (e.g., Open WebUI) *based on available hardware*.
- Create a usable local chat interface; verify the model runs without a cloud AI API.
- Index a local study library: notes, sanitized homelab logs, networking references, Linux guides, certification study materials and self-written walkthroughs.
- Build learning modes: explain a concept; quiz me; give progressively stronger hints; review commands; compare tools; generate a study exercise; evaluate an exercise write-up.
- Make the tutor cite or link to indexed local notes, and distinguish known information from uncertain guesses.
- Learn basic Python integration, local HTTP APIs, prompts, embeddings, vector stores, and service management.
- Protect the system: local binding or authenticated LAN-only access first; protect indexed files; no default root credentials, blanket SSH access or write permissions to the NAS.

**Build sequence**
1. **Hardware audit:** Inventory the Dell and choose bare-metal Linux, Windows, or a lightweight virtualization approach. Do not make Proxmox a blocker unless it improves the AI deployment.
2. **Local model MVP:** Install a suitable runtime/model, run a simple interactive cybersecurity Q&A, record response time and RAM use.
3. **Usable interface:** Add a local chat UI and persistent conversations.
4. **Personal study library:** Index selected offline documents, validate retrieval, and keep sensitive NAS data outside the index.
5. **Tutor workflows:** Flashcards/quizzes, guided troubleshooting, Linux/networking practice, lab-plan review and Markdown notes.
6. **Offline test:** Disconnect upstream internet access temporarily while retaining necessary local connectivity; confirm tutoring and local documents continue to work.
7. **Optional agents later:** Read-only NAS/Proxmox health, media inventory, privacy tasks, recovery reminders, approved security telemetry. Tools should be allowlisted, logged, minimally privileged, and approval-gated for changes.

**Deliverables:** Hardware inventory, model-selection notes, architecture diagram, reproducible deployment notes, sample study sessions, offline test results and secure access controls.

**Done when:** The Dell can run a usable local tutor, answer cybersecurity questions, quiz from local notes and function without a cloud inference service. This comes **before** the red/blue cybersecurity labs.

## Track 2 — Linux, Networking and Virtualization Foundations

**Purpose:** Understand and operate the infrastructure that future labs depend upon. Some basics were already practiced in Track 0.

**Study**
- Linux shell/navigation, processes, systemd, users, groups, sudo, file permissions, cron/systemd timers, packages, logs, Bash.
- Windows administration: PowerShell, services, Event Viewer, users/groups, file shares, networking, basic Sysmon concepts.
- TCP/IP and OSI; IPv4/CIDR, subnetting, routing, ARP, TCP/UDP, ICMP, DNS, DHCP, HTTP(S), SSH, SMB, TLS and NAT.
- VLANs, bridges, firewalls, DNS filtering, VPN concepts, least privilege and network documentation.
- Hypervisors and virtualization: Proxmox VE if hardware and workload requirements make it suitable, KVM, VMs vs containers, virtual switches, disk images, snapshots and templates.
- Separating management, home, media, IoT and intentionally vulnerable lab traffic.

**Projects**
- Build a Linux VM and a Windows evaluation/test VM; practice SSH/PowerShell access and snapshot restoration.
- Draw traffic flow from client → switch/router → NAS and client → reverse proxy/service where applicable.
- Build an isolated virtual network for future lab targets; verify the lab cannot casually reach family devices or NAS shares.
- Create a repeatable base-image/template and a VM inventory.

**Deliverables:** Sanitized topology, VM inventory, networking notes, resource budget and snapshot/restore demonstration.

**Checkpoint:** Explain where packets go, why two machines can or cannot communicate, and how to restore a VM to a known state.

## Track 3 — Python, Bash, APIs and Practical Automation

**Purpose:** Turn repetitive infrastructure work into understandable, testable code.

**Study**
- Python syntax, types, functions, modules, virtual environments, packages, exceptions, files, pathlib, JSON/CSV, regular expressions, argparse, logging and tests.
- Bash and PowerShell fundamentals; exit codes, pipes, scheduled jobs, environment variables.
- REST APIs, authentication, rate limits, pagination, webhooks, Git branches/commits and GitHub documentation.
- Input validation, safe credential handling, idempotency, retries, timeouts, structured logs and dry-run modes.

**Builds**
- NAS health and free-space report.
- Inventory of known devices/services using authorized data.
- Backup verification utility **after** independent backup media is available.
- Parser for sanitized system logs/PCAP metadata with summaries and alerts.
- Small API tools for Home Assistant, Proxmox or Plex using read-only credentials.
- CLI that writes a Markdown lab report with objective, evidence and lessons learned.

**Checkpoint:** Build one documented Python tool with tests, a README, safe configuration and reproducible output.

## Track 4 — Blue Team: Detection, Monitoring and Incident Response

**Purpose:** Learn how defenders observe, identify, investigate and respond to suspicious activity.

**Study**
- Logs and telemetry: Windows Event Logs/Sysmon, Linux journald/auth logs, DNS, firewall, application and network data.
- Wireshark packet analysis: protocols, display filters, conversations, timing, DNS/HTTP/TLS metadata.
- Security monitoring: Wazuh or another SIEM, Suricata, Zeek, agents, sensors and normalized fields.
- Baselines, anomaly detection, alert quality, false positives, event correlation and MITRE ATT&CK mapping.
- Vulnerability inventory, patch management, hardening, host firewalls, least privilege, MFA and response playbooks.
- Incident response lifecycle: preparation, detection, triage, containment, eradication, recovery and lessons learned.
- Introductory digital forensics: hashes, timestamps, timelines, preservation and chain of custody in simulated cases.

**Lab path**
1. Deploy a test Windows/Linux endpoint and collect logs.
2. Send test events into a monitoring platform.
3. Import benign and simulation PCAPs into Wireshark/Zeek/Suricata.
4. Create two clear detection rules, document their assumptions and false-positive cases.
5. Walk through a simulated incident and capture a defensible timeline.
6. Practice a safe recovery action on a snapshot-based VM.

**Deliverables:** Telemetry map, investigation notebook, alert/detection rules, incident report and updated hardening checklist.

## Track 5 — Red Team Foundations and Purple Team Exercises

**Purpose:** Understand attacker thinking *only inside an owned/authorized isolated range*, then translate observations into improvements.

**Study**
- Rules of engagement, scope/allowlists, threat modeling, attack surfaces, reconnaissance and enumeration.
- Kali Linux tooling, Nmap basics and service discovery against intentionally vulnerable VMs.
- Vulnerability validation, exploit concepts, web application testing and OWASP Top 10 labs.
- Authentication, password hashing and authorized offline password auditing.
- Windows/Active Directory concepts, identity misconfiguration, privilege separation and lateral movement theory.
- CTF and intentionally vulnerable practice targets; Metasploit familiarity in a contained range.
- Evidence capture, reporting, risk assessment, defensive recommendations and remediation testing.

**Purple team workflow**
1. Define scope and baseline a test system.
2. Perform an approved, controlled test.
3. Observe endpoint/network logs and detector visibility.
4. Explain the underlying weakness without treating exploitation as the finish line.
5. Harden or patch the target, retest and compare evidence.
6. Write a short attack → detect → improve report.

**Deliverables:** Lab scope document, recon notes, sanitized test evidence, detection gap analysis, remediation report.

## Track 6 — Pwnagotchi and Wi-Fi Security: Red / Blue / Purple

**Dedicated wireless security track, explicitly planned.** Start only when lab scope and isolated/authorized targets are ready.

### A. Foundations and hardware
- Pwnagotchi architecture, appropriate device/adapter selection, firmware, power, display and safe configuration.
- Linux and Python foundations for configuration and plugin work.
- Wi-Fi fundamentals: channels/bands, SSIDs/BSSIDs, beacon/probe/authentication frames, WPA2/WPA3, SAE, PMF, 802.11 management frames.
- Regulatory/ethical scope, test SSIDs, AP allowlists, privacy, capture retention and secure remote administration.

### B. Authorized red-team assessment
- Inventory your **own** test access points and clients.
- Understand what WPA handshakes and PMKID records represent, how capture files are structured and how to verify capture integrity.
- Perform scoped capture collection only on expressly authorized lab Wi-Fi; avoid collecting neighboring users' traffic.
- Learn **offline password auditing with Hashcat** against intentionally chosen test credentials/datasets; compare strong vs weak passphrases and produce remediation guidance.
- Maintain metadata for AP, band/channel, time, target authorization and capture validation.
- Treat disconnection/deauthentication techniques as protocol and detection concepts; don't disrupt real users.

### C. Blue-team wireless defense
- Use a **separate compatible monitoring adapter/sensor**; study Kismet and Wireshark for management-frame and RF-aware visibility.
- Establish a legitimate AP inventory and normal Wi-Fi baseline.
- Analyze safe traces for rogue-AP/evil-twin indicators, unexpected SSIDs/BSSIDs and suspicious disconnect/deauthentication patterns.
- Evaluate WPA2 vs WPA3, PMF support/enforcement, passphrase strength and network segmentation.
- Create a wireless posture scorecard, alert definitions and incident response checklist.

### D. Python and Pwnagotchi plugins
- **Handshake Organizer:** Organize captures by sanctioned AP, timestamp and metadata; deduplicate without logging actual secrets.
- **Capture Validator:** Detect corrupt or insufficient files and record test-only validation results.
- **Wireless Asset Inventory:** Maintain an allowlisted map of lab APs and observed configuration changes.
- **Security Alert Engine:** Produce alerts from passive or replayed monitoring data.
- **Safe Backup/Export:** Retain only needed artifacts; redact personal identifiers and avoid uploading captures to third parties.

### E. Plugin evaluation (review source code before enabling)
- Evaluate projects/plugins including **aircrackonly, hashie, quickdic, handshakes-dl, gps, auto_backup**, and **WireGuard/Tailscale** integrations.
- Document what each plugin does, required privileges, outbound connectivity, data-sharing behavior, dependency status and maintenance history.
- Do not enable auto-upload, automatic attacks or unknown third-party code without understanding its effects.

### F. Purple team integration
- Connect isolated Pwnagotchi exercises and a **separate** wireless monitoring sensor to the Dell analysis environment.
- Use the Raspberry Pi NAS as restricted storage for sanitized records, not as a direct target for experiments.
- Compare observed activity to Wireshark/Kismet logs and Wazuh or equivalent alerts.
- Run the full cycle: assess → detect → document → improve AP settings → retest.

**Five project milestones:** Handshake Organizer → Wireless Asset Inventory → Security Alert Engine → Pwnagotchi Plugin Development → Automated Purple Team Lab.

**Deliverables:** Hardware/firmware notes, authorized-scope checklist, capture validator, inventory and reports, detection rules, privacy review and wireless hardening scorecard.

## Advanced Cybersecurity Specializations — 12 Additional Modules (after local AI)

**Full practical syllabus:** [Red, Blue, and Purple Team Advanced Specializations](red-blue-purple-specializations.md). This adds explicit learning objectives, realistic test labs, recommended tools, deliverables, pass criteria, and a shared investigation capstone. Existing Tracks 4–6 remain the foundational Blue, Red/Purple, and Pwnagotchi/Wi-Fi curriculum; the following modules build on them.

| Module | Specialty | Team / emphasis |
| --- | --- | --- |
| A1 | Threat Hunting | Blue — proactive hypothesis-driven investigations |
| A2 | Adversary Emulation | Red / Purple — authorized MITRE ATT&CK simulations |
| A3 | Detection Engineering | Blue — Sigma, SIEM rules, alert quality and testing |
| A4 | Digital Forensics & Incident Response (DFIR) | Blue — evidence, timelines, triage and recovery |
| A5 | Malware Analysis & Reverse Engineering | Blue / Research — benign sample analysis, Ghidra, YARA |
| A6 | Active Directory & Identity Security | Red / Blue — Kerberos, policies, accounts, logging |
| A7 | Web & API Security Testing | Red / Blue — OWASP methodology on isolated apps |
| A8 | Cloud Security | Red / Blue — AWS IAM, cloud logging, least privilege |
| A9 | Deception Engineering | Blue — isolated honeypots and high-signal alerts |
| A10 | Cyber Threat Intelligence (CTI) | Blue / Purple — TTPs, source confidence, detection ideas |
| A11 | DevSecOps & Supply Chain Security | Red / Blue — scanning, SBOM, secure CI/CD |
| A12 | Breach & Attack Simulation (BAS) | Purple — recurring attack/detection validation |

**Priority once the local AI tutor and lab isolation are ready:** A1 Threat Hunting, A2 Adversary Emulation, A3 Detection Engineering, A4 DFIR, and A6 Active Directory & Identity Security.

**Formal methodologies to study:** MITRE ATT&CK and D3FEND; NIST SP 800-115 and NIST CSF; OWASP WSTG; hypothesis-driven hunting; threat intelligence / Pyramid of Pain; ATT&CK Navigator; repeatable detection-as-code and Purple Team feedback loops. Use [the detailed syllabus](red-blue-purple-specializations.md) for references and lab assessments.

**Integrated investigative capstone:**

1. **Red Team:** Safely simulate a defined ATT&CK-mapped technique on an owned isolated VM.
2. **Blue Team:** Record and correlate defensive telemetry; test detection coverage.
3. **Threat Hunting:** Investigate missed behavior independently using hypotheses and baselines.
4. **DFIR:** Reconstruct an evidence-based timeline from training artifacts.
5. **Purple Team:** Improve a control/detection, retest, and document before/after evidence.
6. **Optional CTI/BAS/AI:** Connect public reporting, repeated validation and local AI-assisted study.

All lab exercises stay scoped, consent-based and isolated from household services. This curriculum is **planned**, not work already completed. The **local AI tutor stays the next project**.

## Track 7 — Privacy, Personal Security and Self-Hosting

**Purpose:** Improve control over personal data and locally hosted services.

**Study**
- Digital footprint/data brokers, lawful removal requests, basic OSINT about one's own exposure and public records.
- Credential hygiene, passkeys/MFA, password managers, device encryption, threat modeling and private backups.
- DNS filtering with Pi-hole or AdGuard Home; browser/DNS privacy fundamentals.
- Self-hosting security: TLS, proxies, authenticated services, updates, service accounts and secure remote-access options.
- Understand the tradeoffs of cloud vs local service, reliability, maintenance and power consumption.

**Projects**
- Maintain a private privacy audit and removal-request tracker.
- Deploy a DNS filter in a test scope; compare allowed/blocked traffic and false positives.
- Create a sanitized security baseline for OMV, Plex and future containers.
- Consider Immich photo storage or a local documentation/knowledge server after evaluating hardware resources.
- Perform 3-2-1 backup planning; defer implementation until a second physical drive exists.

**Checkpoint:** Explain the threat model for each exposed service and demonstrate a repeatable privacy/security review.

## Track 8 — Home Automation, IoT and Smart Access

**Purpose:** Connect and automate home devices while keeping safety, privacy and availability central.

**Study**
- Home Assistant, integrations, automations, MQTT, REST/webhooks and event-driven rules.
- Ring integration capabilities and limitations; local vs cloud control; camera event privacy.
- ESP32/microcontrollers, GPIO, relays, sensors, power safety, BLE, NFC and RFID.
- PoE/IoT camera architecture, segmentation, device identity, monitoring, permissions and logs.
- Access-control principles: fail-safe vs fail-secure, lockout recovery, physical safety and mechanical override.

**Projects**
- Home Assistant dashboard showing permitted device/service states.
- Automation based on authorized Ring or local-camera events.
- ESP32 sensor feeding a local event/logging pipeline.
- Smart room-door access **prototype** using owned NFC/RFID/PIN components, secure enrollment, event logs, local fallback and physical emergency egress.
- Audit and harden an isolated IoT test device/network.

**Checkpoint:** An automation works predictably, can fail safely, and can be explained from trigger to action to log.

## Track 9 — SDR and RF Fundamentals

**Purpose:** Connect prior signal-analysis interests to modern RF and software-defined radio.

**Study**
- Electromagnetic spectrum, wavelength/frequency, sampling, IQ data and waterfalls.
- Antennas, polarization, gain, impedance, bandwidth, link budgets and free-space path loss.
- Modulation: AM, FM, FSK, PSK, QAM and OFDM.
- Noise, SNR/SINR, filters, receiver dynamic range, sensitivity and selectivity.
- Legal passive reception, spectrum rules and responsible handling of received data.

**Projects**
- Begin with a receive-only RTL-SDR and a legal test or public signal source.
- Log spectrum observations with timestamp and receiver settings.
- Receive appropriate weather radio and public ADS-B aircraft transmissions, where permitted.
- Visualize and compare filters, antenna placement and signal quality.
- Create Python scripts for lawful passive RF measurements and graphs.

**Deliverables:** SDR setup notes, signal-identification notebook, waterfall examples and receiver measurement report.

## Track 10 — Weather Satellite Receiving Station

**Purpose:** Build a receive-only station that converts radio signals into weather imagery/data.

**Study**
- Satellite orbits/pass predictions, azimuth/elevation, Doppler shift and antenna choices.
- Satellite downlink frequency identification and legal reception rules.
- Receiver bandwidth, gain, timing, demodulation/decoding and image processing.
- Automation for pass scheduling, recording, decoding, metadata and archiving.

**Projects**
- Predict a pass and verify antenna/receiver preparation.
- Record and decode an appropriate currently receivable weather-satellite signal.
- Archive timestamped imagery and metadata on the NAS.
- Automate the permitted receive/decoding workflow and add status to a dashboard.

**Checkpoint:** Reproduce a satellite reception workflow and explain the signal path and main sources of error.

## Track 11 — Surveillance Technology Awareness and Detection

**Purpose:** Understand what modern surveillance infrastructure does, its technical limits and how to recognize it lawfully.

**Study**
- ALPR/LPR cameras (including Flock-type systems), camera optics, IR illumination, embedded compute, OCR and networking.
- PoE vs cellular backhaul, LTE/5G equipment, local storage vs cloud pipelines and typical camera security surfaces.
- Recognizing hardware by published specifications, public signage, photographs and public transparency data.
- Passive RF survey fundamentals and why signal source attribution is often uncertain.
- Public records, transparency reports and privacy implications; distinguish observations from conclusions.

**Projects**
- Build a **public-information / personally observed** equipment reference database, without exposing private location details.
- Compare hardware architecture of camera and IoT surveillance systems.
- Develop optional computer-vision classification from one's own images and approved datasets.
- Create an ethical/passive-survey note template: source, confidence, limitations and privacy safeguards.

**Boundary:** No tampering, evasion, interference, unauthorized access or attempts to defeat third-party surveillance systems.

## Track 12 — Controlled RF Interference and Resilience

**Purpose:** Understand the physics of interference and jamming **without radiating harmful signals**.

**Study**
- Narrowband/wideband interference, tones, swept signals, adjacent-channel effects and receiver overload.
- Link budgets, BER/PER, SNR, SINR, filtering, rejection, channel occupancy and spectrum interpretation.
- Controlled conducted setups using appropriate coax, attenuators, dummy loads, shielded enclosures and low-power test instruments.
- Anti-interference theory: filtering, robust coding, frequency diversity, spread-spectrum concepts, antenna orientation and shielding.

**Projects**
- Model interference mathematically or simulate it entirely in software.
- If suitable equipment is available, conduct a contained receiver impairment test with no over-the-air harmful emission.
- Record before/after link quality and investigate recovery.
- Write a short report comparing mitigation approaches.

**Checkpoint:** Explain which measurable parameters changed and why; do not build or operate a radiating jammer.

## Track 13 — RF Red / Blue / Purple Team

**Purpose:** Apply attack/defense thinking to RF reliability and monitoring in a lawful contained bench.

**Red-team-style characterization**
- Define safe test scope, characterize an owned receiver and document its limitations.
- Apply software-simulated or strictly conducted/shielded signal impairments.
- Measure reproducible performance changes and protocol behavior.

**Blue-team-style detection**
- Establish a noise floor and normal spectrum baseline.
- Detect anomalies in safe datasets and lab captures.
- Develop alerts based on occupancy, signal level and receiver error rates.
- Test filtering, shielding, placement or protocol configuration mitigations.

**Purple-team loop**
1. Record baseline.
2. Introduce a **contained/simulated** impairment.
3. Detect and characterize change.
4. Apply a mitigation.
5. Retest and compare.
6. Publish a sanitized analysis.

**Checkpoint:** A repeatable RF resilience test and detection/mitigation report.

## Track 14 — Wireless, Embedded Hardware and Cyberdeck

**Purpose:** Learn the interaction between firmware, digital interfaces, wireless protocols and physical devices.

**Study**
- Microcontroller/embedded Linux fundamentals, UART, SPI, I2C, JTAG, flash storage and firmware images.
- Reading schematics, safe voltage/power practices, serial consoles and basic logic-analyzer traces.
- Bluetooth/BLE, RFID, NFC, IR and sub-GHz protocol concepts.
- Proxmark3, Flipper Zero and compatible tools for **owned test tags and systems only**.
- Firmware extraction/review of owned hardware, format inspection and common embedded security mistakes.
- HackRF-class hardware only after RF fundamentals and applicable legal/containment requirements are understood.

**Projects**
- Assemble a **cyberdeck** for learning, documentation and portable authorized diagnostics.
- Interrogate a self-built NFC/RFID access-control demo.
- Examine known/safe test firmware and document configuration/security findings.
- Make a sensor or accessory integration through GPIO/serial.
- Compare Bluetooth/BLE device behaviors with consent and privacy controls.

**Checkpoint:** Demonstrate one hardware protocol and one reproducible firmware or device-security analysis in a controlled environment.

## Track 15 — Local AI Agents and Infrastructure Operations (later expansion)

**Purpose:** Add useful capabilities to the local AI tutor **after** its basic offline tutoring function is stable.

**Study**
- Tool calling, structured JSON outputs, simple agent loops, task planning and constrained execution.
- Read-only service integrations for Proxmox, NAS, Plex, Home Assistant and eventually Wazuh.
- Secure API tokens, service identities, network isolation, audit logs, prompts as untrusted input, and approval gates.
- Evaluation: hallucinations, unsafe tool requests, permission failures, timeout handling and rollback.

**Possible agents**
- **Infrastructure:** NAS health, free disk space, VM state and host load.
- **Media:** Read-only Plex library inventory or metadata hygiene.
- **Automation:** Propose (do not silently perform) Home Assistant actions.
- **Privacy:** Summarize outstanding personal data/privacy tasks.
- **Security Analyst:** Explain approved alerts, correlate sanitized telemetry and quiz response decisions.
- **Recovery:** Remind about backup health and guide restore rehearsal when backup media exists.

**Checkpoint:** A useful read-only agent works with bounded permissions and a visible audit trail. Privileged changes require explicit human approval.

## Track 16 — Mission Control and Long-Term Integration

**Purpose:** Combine working services into one understandable picture of the homelab.

**Dashboard areas (as services actually become available)**
- Dell compute/Proxmox and lab VM status.
- Pi-NAS storage capacity, SMART tests and Docker container health.
- Plex availability and media/storage growth.
- Home Assistant, Ring/local cameras and smart access status.
- Home networking, authorized security sensors, SIEM and incident alerts.
- SDR activity and weather satellite receive jobs.
- Backup status **only after** real independent backups exist.
- AI tutor/agent summaries, explicit proposed actions and audit events.

**Projects**
- Define a structured inventory of services and their dependencies.
- Build a read-only status dashboard with a simple uptime/health history.
- Alert only on actionable changes; suppress duplicate/noisy alerts.
- Write an operator runbook for network outages, failing disks, stopped services and compromised lab VMs.
- Periodically validate security boundaries between home, NAS, media, IoT and test environments.

**Checkpoint:** A dashboard tells what is running, what is broken, why it matters and where to find the documented recovery steps.

---

## Optional certification crosswalk (not a requirement)

These tracks can reinforce knowledge for **CompTIA A+**, **Network+**, **Security+**, **Linux+**, and introductory **AWS** concepts. The projects are pursued for curiosity and hands-on understanding; certifications are optional reference points, not deadlines.

| Knowledge area | Related tracks |
| --- | --- |
| Hardware, operating systems, troubleshooting | 0, 2, 8, 14 |
| IP networking, wireless and protocols | 2, 6, 9 |
| Security controls, logs, risk, incident response | 4, 5, 6, 7 |
| Linux, automation and scripting | 0, 2, 3 |
| Services, virtualization and architecture | 1, 2, 15, 16 |
| RF/signal processing and hardware | 9–14 |

## Suggested immediate return point after the break

1. Power on the Dell OptiPlex 7060 and record hardware resources (CPU, RAM, SSD, GPU/iGPU).
2. Pick the smallest suitable fully local AI stack from real measurements.
3. Get basic model inference and an interactive interface working.
4. Add a cybersecurity tutor workflow with local notes and an offline test.
5. Only **after that**, move into the isolated cybersecurity labs.

## Guiding principle

**Build something interesting → understand it → secure it → break it safely in an approved environment → observe what happened → improve it → document the process.**

No arbitrary deadline. The homelab is a place to experiment and learn.
