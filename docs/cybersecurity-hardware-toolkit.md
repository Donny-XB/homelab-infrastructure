# Techie Cybersecurity Hardware & Tooling Curriculum

**Status:** Planned learning toolkit, expanded 2026-10-14.  
**Priority:** The fully local AI tutor on the Dell OptiPlex 7060 remains the **next major build**. This toolkit is a future branch of the curriculum, not a current shopping list or a record of equipment already owned.

**Related:** [Master Curriculum](learning-agenda.md) · [Red/Blue/Purple Specializations](red-blue-purple-specializations.md) · [Local AI Plan](../ai/README.md)

## Why a separate hardware track?

Security research spans **networking, wireless, RFID/NFC, radio, USB, physical access, embedded firmware, and hardware signals**. Different tools answer different questions. Buying a multi-tool does not replace understanding protocols, legal authorization, electrical safety, scope, and what a measurement actually proves.

We will learn the **underlying technology first**, then use suitable equipment in **owned, isolated, authorized** tests. Tools below are **candidates to study**, not claimed purchases, commitments, or necessary prerequisites.

## Toolkit map

| Category | Tool(s) to study | What it teaches | Safe demonstration / portfolio artifact |
| --- | --- | --- | --- |
| Multiprotocol exploration | **Flipper Zero** | NFC/RFID basics, infrared, supported sub-GHz protocols, GPIO and device interaction | Examine a self-issued NFC tag, compare read-only metadata and permissions, document a mock IR appliance protocol |
| RFID/NFC specialist | **Proxmark3** (e.g., RDV family), **ChameleonUltra** (optional) | Low- and high-frequency RFID, NFC, tag protocols, credential system design and reader behavior | Inventory owned training tags and write a risk review of a deliberately built access-control prototype |
| Wi-Fi field research | **Pwnagotchi** with compatible hardware and firmware | 802.11 management frames, WPA authentication concepts, Linux/Python plugins, capture validation | Analyze permitted test captures, maintain a scoped AP inventory and build a read-only validation/backup plugin |
| Wi-Fi monitoring | Compatible **monitor-mode USB Wi-Fi adapter**, separate monitoring sensor | Kismet/Wireshark visibility, wireless beacons, channel selection, WPA2/WPA3/PMF and anomaly detection | Passive authorized WLAN baseline and suspected-rogue-AP detection using replayed/sanitized records |
| Wireless audit appliances | **WiFi Pineapple** (optional, later) | AP inventory, association behavior, wireless assessment methodology and defenses | Evaluate owned test AP security within a lab-only SSID; produce mitigation and monitoring checklist |
| Passive RF receive | **RTL-SDR** | Spectrum basics, IQ samples, gain, filtering, antennas, modulation, public lawful receive-only signals | Receive permitted weather radio/ADS-B; build waterfall and signal-identification log |
| Advanced SDR | **HackRF One**, **PortaPack** (optional), suitable RF lab fixtures | Wideband SDR architecture, receiver chains, waveform processing and contained lab signal generation | Compare two recorded or conducted/shielded test signals; document spectral differences and regulatory constraints |
| RF measurements | **tinySA**, suitable antenna, attenuators, filters, dummy loads and cables | Frequency response, receiver noise, gain, filtering and test setup calibration | Measure a lawful test source or contained bench signal and compare filter responses |
| Sub-GHz protocol education | **YARD Stick One** (optional), owned training modules | Protocol framing, FSK/OOK concepts and robustness of simple radio links | Decode a personally generated test waveform offline and explain frame fields |
| USB and HID awareness | **USB Rubber Ducky**, **O.MG Cable** (optional training hardware) | USB enumeration, HID trust, peripheral risk, endpoint controls | On a disposable owned VM/test machine, demonstrate a harmless typed text payload and verify logging/USB policies; never conceal devices in others' environments |
| Network implant/appliance awareness | **LAN Turtle** (optional), lab test network interfaces | Inline network appliances, unexpected Ethernet devices, device inventory and detection | Build a mock unauthorized-device alert on isolated switch/VM telemetry; never deploy covertly |
| Embedded buses and debugging | **Bus Pirate**, logic analyzer, USB-UART adapter, oscilloscope (optional) | UART, SPI, I²C, GPIO, serial consoles, signals and firmware interfaces | Read diagnostic output from an owned ESP32/development board; save and annotate a timing diagram |
| Hardware debug interfaces | **JTAGulator** (optional), JTAG/SWD probe, SOIC clip or SPI flash programmer | Discovery of debug pins, flash images, firmware integrity and secure boot concepts | Identify documented debug headers on an owned dev board; examine a harmless training firmware image |
| Hardware side-channel research | **ChipWhisperer** (advanced optional) | Power/timing leakage, measurement noise and countermeasure concepts | Analyze provided training traces or an owned demo target in a contained setup |
| Prototyping and access control | **ESP32**, NFC/RFID modules, relays, sensors, bench power supply | BLE, GPIO, microcontrollers, access logs, mechanical safety and least privilege | Build a lock-controller prototype using training credentials with safe/manual egress |
| Portable study station | **Cyberdeck** (custom build) | Portable Linux, radios, battery/power planning, USB peripherals, field documentation | Assemble a portable offline documentation and receive-only/authorized diagnostics workstation |
| General hardware essentials | Multimeter, ESD protection, breadboard, proper cables, labeled storage | Voltage/current safety, pinout reading, repeatability and handling | Hardware inventory, wiring diagrams, power budget and test checklist |

### Notes on tool capabilities

- **Flipper Zero:** Useful educational multi-tool, **not** a universal key, cloning solution, or replacement for a full RFID/RF laboratory. Capabilities vary by protocol, hardware, firmware and regional restrictions.
- **Proxmark3:** Deeper RFID/NFC examination than a general-purpose multi-tool; tag access controls and cryptography still matter. Do not presume that every card can be read or emulated.
- **Pwnagotchi:** Its compatibility depends on specific device, Wi-Fi hardware and maintained firmware/plugins. It should **not** be casually installed on the Raspberry Pi that is already serving OMV/Plex.
- **HackRF One:** Advanced SDR hardware with transmit capability; any transmit-side experiments must obey law and use proper contained/conducted configurations. No radiating jammer projects.
- **USB/inline network specialty tools:** Teach how hosts and defenders respond to unexpected peripherals and interfaces. Their lab curriculum emphasizes **detection, consent and containment**, not covert access.

## Module H1 — Flipper Zero and multiprotocol fundamentals

**Learn:** LF RFID vs HF NFC; credential identifiers vs actual authentication; IR signal formats and timing; sub-GHz fundamentals; basic GPIO; firmware ecosystems; responsible disclosure and permissions.

**Exercises**
1. Catalog a handful of **owned training tags** and record which information is publicly readable and which operations require authentication.
2. Capture and compare a simple IR transmission from a device you own (for example, a test remote), then diagram the message format.
3. Read a supported development-board GPIO signal and verify voltage compatibility.
4. Create a security comparison of IR, RFID, NFC, BLE and sub-GHz technologies without assuming interchangeable attacks.

**Deliverable:** `hardware/flipper-zero/` lab notes: protocol matrix, screenshots/observations, diagram, safety and device scope.

**Definition of done:** Explain the device's real capabilities and limits, and describe how a defender designs an access system that doesn't rely only on a static identifier.

## Module H2 — Proxmark3, NFC, and owned access-control systems

**Learn:** Reader/tag roles, LF/HF technologies, anti-collision, key management, challenge-response, replay concepts, enrollment lifecycle, access-log review and badge deprovisioning.

**Exercises:** Read metadata from owned demo tags; compare two training credential technologies; use a self-built reader to collect authorization decisions and identify weak design choices. Never use live workplace, transit or third-party access badges as experiments.

**Deliverable:** Test-badge inventory, mock door-access threat model, reader flowchart and before/after security checklist.

**Definition of done:** Show how a secure credential verification design differs from merely trusting a badge ID.

## Module H3 — Wi-Fi auditing, Pwnagotchi and monitoring sensors

**Learn:** Channels/bands, 802.11 management frames, beacon/probe frames, WPA2/WPA3 handshake *concepts*, PMKID validation, PMF and rogue AP awareness.

**Projects:** Dedicated compatible Pwnagotchi device; separate Kismet/Wireshark sensor; authorized AP allowlist; analysis of owned or generated training capture files; Python organizer/validator, metadata deduplication and backup controls; separate blue-team alerting dashboard.

**Optional tools:** Monitor-mode Wi-Fi adapter; WiFi Pineapple *only when isolated testing adds a learning objective*. Use offline Hashcat auditing against deliberately chosen test data as described in the [wireless curriculum](learning-agenda.md#track-6--pwnagotchi-and-wi-fi-security-red--blue--purple).

**Deliverable:** Wireless baseline, monitored test AP inventory, test-capture validator, privacy review and hardening scorecard.

**Definition of done:** Correlate a controlled wireless test's observations across sensors without disrupting unrelated networks.

## Module H4 — RTL-SDR, HackRF, RF measurement and spectrum awareness

**Learn:** IQ/waterfall interpretation, AM/FM/FSK/PSK/QAM/OFDM fundamentals, antennas, gain, path loss, receive selectivity and RF interference detection.

**Projects:** Receive lawful public signals; analyze a prepared RF recording; compare antennas/filters; decode an appropriate weather-satellite signal; model noise and interference in software; perform only properly contained lab impairments, if necessary.

**Optional tools:** RTL-SDR first; tinySA and measurement accessories as needs arise; HackRF/PortaPack/YARD Stick One later, subject to capability and legal constraints.

**Deliverable:** Annotated waterfall, frequency/signal journal, receiver block diagram and RF resilience report.

**Definition of done:** Explain the evidence behind identification of a signal and distinguish a measured observation from speculation about the transmitter.

## Module H5 — USB, HID and physical-device security

**Learn:** USB enumeration, HID keyboards, device trust, endpoint control, port permissions, hardware implants as a threat model, and physical-access logging.

**Projects:** Inspect device inventories and USB audit trails; on a disposable test workstation, run a harmless HID demo that types only a known marker phrase; create alert logic for unapproved peripherals; draft an incident response checklist for a discovered unknown cable/device.

**Optional tools:** USB Rubber Ducky, O.MG Cable, LAN Turtle *for defensive study and explicitly scoped test demonstrations*. These are not needed for the foundational cybersecurity curriculum.

**Deliverable:** USB trust-boundary map, audit logs, detection rules and a physical-media handling SOP.

**Definition of done:** Demonstrate detection or prevention of an unexpected peripheral on owned equipment and document false positives.

## Module H6 — Embedded debugging and firmware analysis

**Learn:** Pins, voltage levels, UART, SPI, I²C, JTAG/SWD, bootloaders, device firmware formats, debug exposure and flash security.

**Projects:** Connect a USB-to-serial adapter to an owned dev board; capture its own diagnostics; interpret a logic-analyzer waveform; inspect a self-compiled firmware binary; compare debug-interface restrictions with expected secure-product practice.

**Optional tools:** Multimeter and USB-UART first; then logic analyzer/Bus Pirate; JTAG adapter or JTAGulator; specialized flash tools; advanced ChipWhisperer only for focused research.

**Deliverable:** Pinout/voltage notes, bus capture, reproducible firmware-inspection report and suggested hardening controls.

**Definition of done:** Explain what a physical interface exposes and how a product design can restrict it.

## Module H7 — Cyberdeck and portable incident-response kit

**Learn:** Laptop/mini-PC vs SBC choices, portable power and safety, Linux images, offline notes, network adapter compatibility, cable management, evidence protection and operational checklists.

**Projects:** Design a portable kit for **documenting authorized assessments**, viewing local dashboards, collecting benign data and performing receive-only RF exploration. Build only what solves a practical recurring use case.

**Deliverable:** Bill of materials, architecture, power budget, secure-storage plan, field runbook and demonstration.

**Definition of done:** Operate the toolkit offline in a controlled test with repeatable documentation.

---

## How this hardware fits Red, Blue and Purple Teams

| Tool family | Red team (owned test systems) | Blue team | Purple team |
| --- | --- | --- | --- |
| Flipper / Proxmark / NFC | Evaluate a purpose-built access prototype | Review reader logs, enforce strong credential verification | Validate improvement after replacing weak credential assumptions |
| Pwnagotchi / Wi-Fi adapter / Pineapple | Scoped wireless configuration assessment | Kismet, Wireshark and AP hardening | Compare test telemetry and PMF/segmentation policies |
| RTL-SDR / HackRF / spectrum tools | Characterize a contained test receiver | Establish spectrum and interference baselines | Measure before/after RF resilience |
| USB Rubber Ducky / O.MG / LAN Turtle | Benign test-device simulations, with consent | USB/network device inventory and endpoint controls | Test whether unexpected peripherals trigger useful detection |
| Bus Pirate / JTAG / logic analyzer | Review debug exposure on owned dev boards | Firmware integrity and hardware configuration checks | Close exposed debug pathways and retest |
| Cyberdeck | Portable authorized documentation | Portable diagnostics / incident response | Reproduce tests and share evidence |

## Recommended progression — not a shopping checklist

**Tier 0 — Use what is already available:** Dell, Raspberry Pi NAS, Windows workstation, virtual machines, GitHub and a local AI tutor; learn protocols in software before buying hardware.

**Tier 1 — Low-complexity physical fundamentals:** Owned ESP32/dev board, NFC test tags, USB-UART adapter and a multimeter. Add Flipper Zero **if** its multiprotocol labs are interesting enough to justify it.

**Tier 2 — Specialization by curiosity:** Proxmark3 for RFID; suitable Wi-Fi adapter/Pwnagotchi for WLAN; RTL-SDR for receive-only RF; logic analyzer/Bus Pirate for embedded diagnostics.

**Tier 3 — Deeper investigations:** HackRF/PortaPack, WiFi Pineapple, USB Rubber Ducky, LAN Turtle, O.MG Cable, JTAGulator, ChipWhisperer and a cyberdeck only if a specific exercise needs them.

**Buy/select based on:** supported protocols and frequencies, maintained firmware, Linux/Windows driver compatibility, learning value, risk, cost and test-environment requirements. Do not assume a tool solves a problem merely because it appears in a video.

## Tool-independent methodologies

Every hardware lab should follow:

1. **Question & scope:** Name the owned test device and define allowed operations.
2. **Protocol & threat model:** Understand what each interface is actually doing.
3. **Baseline:** Record expected operation and the device's normal telemetry.
4. **Controlled assessment:** Run only scoped, lawful, non-disruptive tests or offline analysis.
5. **Blue-team observations:** Examine reader/endpoint/network/radio logs and identify gaps.
6. **Remediation and retest:** Improve the configuration/design and compare outcomes.
7. **Documentation:** Store only sanitized notes, example data and findings in GitHub.

**Privacy/security:** Do not publish RF capture files containing others' transmissions, real badge secrets, unredacted packet captures, passwords, personal MAC addresses, or identifiable household security details. Do not connect intentionally vulnerable hardware to the production NAS or expose device admin panels to the internet.

> **Next action remains unchanged:** Finish the **fully local AI tutor** first. Then select a hardware track by interest and build the smallest controlled experiment needed to learn it.
