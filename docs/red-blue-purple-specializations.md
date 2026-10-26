# Techie Cybersecurity — Advanced Red, Blue, and Purple Team Specializations

**Status:** Planned curriculum expansion · learning priorities updated 2026-10-25  
**Sequence:** Build the offline-capable AI cybersecurity tutor on the Dell OptiPlex 7060 **first**. The modules here begin after that milestone and can be explored in any order that fits the lab's resources and the user's interests.

This is a hands-on, investigation-oriented curriculum. Rather than collecting tools, each module asks: **What am I trying to understand? What can I observe? How would I verify it? How would I improve a system?**

See [Complete Learning Curriculum](learning-agenda.md), especially its Linux/network foundations, Blue Team, Red/Purple Team, and Pwnagotchi/Wi-Fi modules. This guide **extends** those tracks; it does not replace them.

## Complementary Cybersecurity Hardware Track

See the [Cybersecurity Hardware & Tooling Curriculum](cybersecurity-hardware-toolkit.md) for hardware-focused Red/Blue/Purple exercises involving Flipper Zero, Proxmark3, RFID/NFC, Pwnagotchi, Wi-Fi Pineapple, RTL-SDR/HackRF, USB Rubber Ducky, O.MG Cable, LAN Turtle, embedded debugging and a cyberdeck. Its equipment is optional, selected only when the underlying protocol and test environment justify it. The **local AI tutor remains the next build**, before cybersecurity labs.

## Operating rules and progression

- **Authorized scope only.** Offensive labs use explicitly owned or authorized VMs, demo applications, synthetic identities, controlled containers or public training ranges with permission. No scans, captures or tests against neighbors or third parties.
- **Isolate risky work.** Use dedicated VM networks and snapshots. Do not bridge deliberately vulnerable machines into the household LAN or connect them routinely to the personal NAS.
- **No live malware on normal systems.** Malware analysis is performed in a genuinely isolated environment, initially using static samples, benign simulations and training datasets.
- **Separate roles.** Use a dedicated lab identity rather than reusing administrator or personal SMB credentials; keep evidence sanitized.
- **Work with evidence.** Capture baselines, observations, false positives, defensive changes and a retest for every significant exercise.
- **Learning order:** *local AI tutor* → basic virtual network and telemetry → threat hunting and detection engineering → safe adversary simulation → forensics/purple-team validation → specialty tracks.
- **Hardware reality:** A Dell OptiPlex 7060 may not have RAM/CPU capacity for multiple simultaneous VMs or heavyweight SIEMs; measure it before selecting tools and reduce the lab footprint as needed.

## Module overview

| # | Specialization | Perspective | Example deliverable |
| --- | --- | --- | --- |
| A1 | Threat Hunting | Blue | Hypothesis-driven hunt report |
| A2 | Adversary Emulation | Red / Purple | ATT&CK-mapped simulation plan and evidence |
| A3 | Detection Engineering | Blue | Tested detections with false-positive notes |
| A4 | Digital Forensics & Incident Response (DFIR) | Blue | Forensic timeline and response playbook |
| A5 | Malware Analysis & Reverse Engineering | Blue / Research | Benign sample behavioral analysis |
| A6 | Active Directory & Identity Security | Red / Blue | Hardened test domain and detection map |
| A7 | Web & API Security Testing | Red / Blue | Authorized OWASP assessment report |
| A8 | Cloud Security | Red / Blue | Sandbox IAM and logging security review |
| A9 | Deception Engineering | Blue | Isolated honeypot/decoy telemetry |
| A10 | Cyber Threat Intelligence (CTI) | Blue / Purple | Actor technique profile and detection ideas |
| A11 | DevSecOps & Software Supply Chain | Red / Blue | Secure sample CI pipeline and SBOM |
| A12 | Breach & Attack Simulation (BAS) | Purple | Reproducible detection validation scorecard |

**Updated depth priorities (2026-10-25):** This detailed syllabus is a reference library, **not twelve mandatory deep courses**. The [master depth matrix](learning-agenda.md#personalized-cybersecurity-learning-depths-updated-2026-10-25) is authoritative.

- **Go deep:** A1 Threat Hunting, A2 Adversary Emulation within Red Team, A4 DFIR, A5 Malware Analysis & Reverse Engineering (**later**, after isolated analysis infrastructure), A7 Web/API Security, and A10 CTI/OSINT. A3 Detection Engineering is developed deeply **as a practical part of hunting and defense**, rather than a disconnected prerequisite. Network security/reconnaissance and AI/LLM security are also deep tracks in the master curriculum.
- **Working knowledge:** RF/SDR/wireless and hardware/embedded are covered by the master and hardware guides, with short demos rather than all advanced extensions.
- **Just explore:** A8 Cloud Security — one small authorized IAM/log analysis experiment; no large cloud certification path.
- **Supporting, as needed:** A6 identity/AD, A9 deception, A11 DevSecOps, A12 BAS. Use these when they solve a real question in a deep-track project; don't require their whole syllabus.

**Language timing:** Python early for network automation/analysis; Bash and PowerShell in the corresponding operating-system labs; HTML/CSS/JavaScript, PHP and SQL during actual web/API builds and security tests; **C → C++ → Assembly only when the later malware/reversing lab needs them**. Java/TypeScript remain optional context-driven additions.

**Unit of progress:** A real homelab use case → small safe build → observe evidence → test in an authorized isolated scope → defend/remediate → document → decide whether to deepen.

---

## A1 — Threat Hunting

**Central question:** What happened that nobody alerted on?

**Learning objectives**
- Differentiate intelligence-led, hypothesis-led and anomaly-led hunts from reactive alert triage.
- Form a falsifiable hunt hypothesis grounded in a risk, asset, technique or suspicious observation.
- Query endpoint, authentication, DNS, network and application logs using time ranges, normal baselines and event context.
- Recognize missing telemetry, alternative explanations and false positives.
- Record hunt outcomes, propose a new detection, and decide what merits escalation.

**Tools / references:** Sysmon, Windows Event Viewer, Linux journald, Wireshark, Zeek, Wazuh or a lightweight log stack; MITRE ATT&CK; optionally Sigma and Python notebooks.

**Hands-on lab:** Generate normal login, process-execution and network behavior on an isolated Windows/Linux VM; add pre-labeled benign simulated suspicious events using approved datasets or simulation tooling. Hunt for unusual process ancestry, service changes, off-hours sign-ins or DNS outliers. Compare the hunt hypothesis to evidence.

**Deliverables:** Hunt hypothesis, query notebook, baseline description, timeline, findings, blind spots, and one candidate detection rule.

**Complete when:** You can explain why an event is or is not suspicious, independently of whether a SIEM raised an alert.

## A2 — Adversary Emulation

**Central question:** Can we safely reproduce and observe behaviors described in real intrusions?

**Learning objectives**
- Distinguish an indicator from a tactic, technique and procedure (TTP).
- Read ATT&CK technique descriptions and write a narrow, authorized test objective.
- Design emulation plans with scope, prerequisites, rollback, logging and stop conditions.
- Use benign/non-destructive simulations to study behavioral observability, not merely tool signatures.
- Compare expected vs observed telemetry and map test artifacts to detections and mitigations.

**Tools / references:** MITRE ATT&CK, Atomic Red Team test documentation, MITRE CALDERA (only after isolation and resources are validated), EDR/Sysmon lab telemetry, snapshots.

**Hands-on lab:** Select a safe persistence- or discovery-themed simulated behavior on an owned VM, establish a snapshot, enable logging, perform the approved test, collect Sysmon/Zeek/SIEM observations, and roll back. Record which ATT&CK behavior was actually represented and which parts were not.

**Deliverables:** Emulation plan with rules of engagement, ATT&CK mappings, observable events, rollback evidence and a gap analysis.

**Complete when:** A simulation is repeatable, produces identified defensive telemetry, and has documented safe recovery steps.

## A3 — Detection Engineering

**Central question:** How can a suspicious behavior become a dependable alert?

**Learning objectives**
- Separate detection logic from alert handling, enrichment and response.
- Choose meaningful event fields, baselines, thresholds and time windows.
- Author and test Sigma-style logic, SIEM queries or Suricata signatures for benign lab events.
- Evaluate false positives, false negatives, coverage, performance and data prerequisites.
- Version detection rules as code and document why they work and when they fail.

**Tools / references:** Sigma, Wazuh rules, Sysmon, Zeek, Suricata, YARA (for file-content analysis), Git, Python unit/fixture tests, ATT&CK and D3FEND.

**Hands-on lab:** Build detections for a synthetic suspicious login pattern, unusual child-process chain and network anomaly; test against recorded benign and simulation datasets. Revise thresholds and measure coverage.

**Deliverables:** Detection-as-code repository section, test fixtures, detection rationale, false-positive catalog, triage checklist and a versioned change log.

**Complete when:** A detection is tested with both positive and negative cases and another learner could reproduce your result.

## A4 — Digital Forensics & Incident Response (DFIR)

**Central question:** What happened, how do we prove it, and how should we recover?

**Learning objectives**
- Understand acquisition, integrity hashing, event chronology, evidence handling and chain of custody.
- Use filesystem timestamps, Windows event artifacts, Linux logs and process/network data to form a timeline.
- Understand volatile vs persistent artifacts and why evidence collection can change a system.
- Distinguish triage, containment, eradication, recovery and post-incident lessons.
- Practice reporting facts separately from hypotheses.

**Tools / references:** Autopsy, Velociraptor (as resources permit), Volatility 3 with prepared training memory images, KAPE/Plaso concepts, Windows Event Logs, Linux audit/journal logs, hash utilities.

**Hands-on lab:** Investigate a prepared training disk/memory image or an owned snapshot with a simulated suspicious change. Verify evidence hashes, reconstruct a timeline, classify confidence and write a short incident response plan.

**Deliverables:** Evidence inventory, integrity/hash manifest, incident timeline, root-cause hypotheses, containment plan and lessons-learned report.

**Complete when:** The incident narrative follows evidence and identifies uncertainty rather than inventing missing facts.

## A5 — Malware Analysis & Reverse Engineering

**Central question:** What does an unknown program do, and how can we detect its behavior?

**Learning objectives**
- Learn executable structure, strings, metadata, imports, hashing and signing concepts.
- Understand static vs dynamic analysis, control flow, process trees, persistence, network indicators and obfuscation.
- Read simple disassembly/decompiler output; understand limits and uncertainty.
- Relate observed behaviors to detections, mitigations and forensic artifacts.
- Design rigorous containment: no personal accounts, no shared folders, no bidirectional clipboard, no trusted network access, no accidental upload of sensitive samples.

**Tools / references:** Ghidra, Detect It Easy, strings/file/sha256 utilities, Procmon and Process Explorer on an isolated test VM, Wireshark with safe simulated traffic, YARA; benign training binaries and purpose-built samples first.

**Hands-on lab:** Compile a small benign program that writes a file and makes a documented local test request. Inspect it statically, analyze it in a detached sandbox, document expected vs observed behavior, and write a YARA rule matching your own program (with false-positive test cases).

**Deliverables:** Static/dynamic analysis notes, annotated control-flow observations, sample hash, behavioral summary and a defensive detection rule.

**Complete when:** You can describe a program's observable behavior without executing unknown code on a personal or NAS system.

## A6 — Active Directory & Identity Security

**Central question:** How do identities, permissions and trust relationships become attack surfaces?

**Learning objectives**
- Understand domains, controllers, Kerberos, NTLM, LDAP, DNS, group policy, service accounts, delegated administration and domain trust basics.
- Explain the effects of account misuse, password policy, excessive group membership and identity misconfiguration.
- Audit a small controlled domain with simulated users, roles, policies and logons.
- Map identity behaviors to relevant event logs, detections, controls and least-privilege improvements.
- Practice safe remediation and recovery without using household identities.

**Tools / references:** Windows Server evaluation images (when practical), Windows client VM, PowerShell/RSAT, Sysmon, Windows Event Forwarding/Wazuh, Microsoft security baselines, ATT&CK identity-related techniques.

**Hands-on lab:** Create a toy domain with fictional users and roles, examine group membership and authentication events, intentionally introduce a simple over-permissioned test group, then correct it and verify access boundaries. Simulate approved account anomalies to exercise detection logic.

**Deliverables:** Identity topology diagram, OU/group policy plan, least-privilege review, authentication event map and remediation checklist.

**Complete when:** You can explain domain authentication flows, detect test account anomalies and demonstrate reduced privilege without breaking business-as-usual test workflows.

## A7 — Web and API Security Testing

**Central question:** Do our web services enforce their own security rules correctly?

**Learning objectives**
- Understand HTTP methods/status codes, sessions, cookies, TLS, authentication vs authorization, CSRF, CORS, input validation, REST/JSON and API access control.
- Apply OWASP Web Security Testing Guide concepts systematically to a training application.
- Identify how broken object authorization, injection, insecure file handling and session issues appear in a controlled environment.
- Learn reporting, risk ranking, secure implementation patterns and retesting.

**Tools / references:** OWASP WSTG, OWASP Juice Shop, WebGoat, OWASP ZAP, Burp Suite Community, Postman/Insomnia, browser developer tools.

**Hands-on lab:** Deploy an intentionally vulnerable web app in an isolated container/VM with only authorized access; inventory endpoints, complete a guided OWASP lesson, document one finding without publishing exploitation of real services, apply/describe a mitigation and retest.

**Deliverables:** Scoped test plan, endpoint map, findings with evidence, severity rationale, remediation and retest note.

**Complete when:** You can explain the control that failed and demonstrate that the specific test case is addressed.

## A8 — Cloud Security (AWS-focused)

**Central question:** What changes about identity, visibility and misconfiguration when infrastructure is managed by a cloud provider?

**Learning objectives**
- Understand shared responsibility, IAM roles/policies, least privilege, VPC segmentation, object-storage permissions, KMS, audit logging and security monitoring.
- Interpret CloudTrail, VPC Flow Logs, AWS Config/Security Hub/GuardDuty concepts and billing implications.
- Compare on-prem logs/network boundaries to cloud-native equivalents.
- Model a cloud threat scenario and assess controls using synthetic or sandbox data.

**Tools / references:** AWS learning account with strong billing guardrails where feasible, IAM policy simulator, AWS CLI, CloudTrail, IAM Access Analyzer, CloudFormation/Terraform concepts; local/cloud emulators or provided labs where a live cloud account is undesirable.

**Hands-on lab:** In a disposable sandbox, create a minimal role with narrowly scoped S3 access, test expected allow/deny decisions, review an example audit event, and create a cost-cleanup checklist. Alternatively use prepared IAM policy and CloudTrail datasets offline.

**Deliverables:** IAM least-privilege policy analysis, architecture/threat model, audit interpretation and deletion/cost checklist.

**Complete when:** You can reason about least privilege and audit trails without exposing a real cloud account or leaving unintended billable resources.

## A9 — Deception Engineering

**Central question:** Can a believable decoy produce high-signal alerts without creating additional risk?

**Learning objectives**
- Distinguish honeypots, honeynets, honeytokens and decoy credentials.
- Understand containment, logging, safety, legal/ethical issues and alert confidence.
- Separate decoy telemetry from production secrets and avoid accidentally exposing interactive vulnerable services.
- Correlate a decoy interaction with host/network indicators.

**Tools / references:** OpenCanary, Cowrie (isolated and configured for safety), T-Pot concepts when resources permit, Zeek/Wazuh, simple mock services.

**Hands-on lab:** Put a decoy service in an isolated network, connect from a second owned test VM, record telemetry and set up a local alert. Compare decoy events with legitimate operational data.

**Deliverables:** Decoy threat model, network boundary verification, one actionable alert, telemetry example and safe shutdown plan.

**Complete when:** The decoy detects controlled interactions without providing access to real secrets or increasing production attack surface.

## A10 — Cyber Threat Intelligence (CTI)

**Central question:** How can external reporting become a useful defensive decision?

**Learning objectives**
- Differentiate strategic, operational and tactical intelligence, and IOCs versus TTPs.
- Use source evaluation, uncertainty, freshness and confidence ratings.
- Interpret reports about actor behavior without treating attribution as certainty.
- Map described behaviors to ATT&CK and derive defensive questions/detection opportunities.
- Learn indicator lifecycle, STIX/TAXII concepts, sharing/privacy considerations and the Pyramid of Pain.

**Tools / references:** MITRE ATT&CK, CISA advisories, publicly documented threat reports, MISP/OpenCTI concepts, STIX examples and Sigma.

**Hands-on lab:** Select a public threat report and produce a one-page profile: attack sequence, ATT&CK mapping, evidence strength, relevant controls, and two testable hunting hypotheses for your *own* environment.

**Deliverables:** Source bibliography, ATT&CK technique matrix, confidence notes, prioritized detection backlog and defensible intelligence brief.

**Complete when:** A threat report produces testable defensive work rather than an unverified list of indicators.

## A11 — DevSecOps and Software Supply Chain

**Central question:** Can we keep security controls running while code moves from development into deployment?

**Learning objectives**
- Understand CI/CD, code review, branches, reproducible builds, dependency risks, SBOMs and code signing concepts.
- Distinguish static analysis, dynamic testing, software composition analysis, container scanning and secret detection.
- Analyze Dockerfile/Compose permissions, base-image provenance, least privilege and patch lifecycle.
- Learn provenance/artifact integrity, secret management, safe updates and rollback.

**Tools / references:** GitHub Actions or local CI, Semgrep, CodeQL concepts, Trivy, Gitleaks, CycloneDX/SPDX, Dependabot concepts, Docker Scout alternatives and OWASP guidance.

**Hands-on lab:** Create a tiny toy Python API, add unit tests and a CI workflow that checks code, dependencies, secrets and container config; fix a deliberately introduced harmless insecure dependency/configuration example.

**Deliverables:** Example app, dependency inventory/SBOM, security checks, failure/recovery demonstration and release/update checklist.

**Complete when:** A predictable unsafe change is flagged by the pipeline, and the fixed version passes.

## A12 — Breach & Attack Simulation (BAS)

**Central question:** Do our controls still detect the agreed-upon scenarios over time?

**Learning objectives**
- Compare BAS, adversary emulation and full penetration testing; understand their different goals.
- Develop a repeatable library of authorized, non-destructive test cases mapped to ATT&CK behaviors.
- Define telemetry requirements and expected alerts before running a test.
- Score coverage, time to detect, alert quality and regression over repeated runs.
- Report gaps, assign remediations, retest and maintain versioned evidence.

**Tools / references:** Atomic Red Team test catalogs, MITRE CALDERA in an isolated lab, SIEM/EDR data, Python test harnesses, Sigma and ATT&CK Navigator.

**Hands-on lab:** Choose three harmless test scenarios in a dedicated VM; execute them with snapshots and documented scope; compare which generate alerts, which create telemetry but no alert, and which are invisible. Improve one detection and rerun.

**Deliverables:** BAS scenario catalog, preconditions, expected outputs, detection coverage matrix, false-positive notes and regression report.

**Complete when:** One test can be rerun later and meaningfully demonstrates whether defensive coverage improved or degraded.

---

## Formal frameworks and structured approaches

Frameworks are **lenses for conducting work**, not competing sets of commands. Learn when each is appropriate.

| Framework / methodology | Primary purpose | Curriculum use |
| --- | --- | --- |
| [MITRE ATT&CK](https://attack.mitre.org/) | Describe adversary tactics and techniques | Map tests, threat hunts, and detections |
| [MITRE D3FEND](https://d3fend.mitre.org/) | Describe defensive techniques and countermeasures | Explore what control might address a tested behavior |
| [NIST SP 800-115](https://csrc.nist.gov/pubs/sp/800/115/final) | Plan and report technical security testing and assessment | Scope, authorize, execute, document and report assessments |
| [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) | Structured web application and API security assessment | Web/API test planning and evidence |
| [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework) | Organize cybersecurity governance, identification, protection, detection, response and recovery | Create a holistic defensive capabilities checklist |
| [MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) | Visualize ATT&CK coverage and gaps | Compare observed behaviors and detection coverage |
| [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) | Library of ATT&CK-mapped tests | Controlled, scoped behavioral test inputs |
| [MITRE CALDERA](https://caldera.mitre.org/) | Automated adversary emulation research | Later-stage authorized lab exercises with safe scope |
| [Sigma](https://sigmahq.io/) and [YARA](https://virustotal.github.io/yara-x/docs/writing_yara_rules/) | Portable log detections and file-pattern matching | Detection engineering and sample analysis |

Also study the **Pyramid of Pain**, detection lifecycle, and a **hypothesis-driven threat hunting** process to understand why detecting behaviors can be more resilient than blocking a single hash or IP address.

## Capstone — One investigation, five viewpoints

**Scenario:** A fictional organization has two isolated lab VMs and a monitoring sensor. Controlled test behavior generates suspicious process, authentication and network activity. The exercise is self-contained, owned and reversible.

### Investigation sequence

1. **Red Team / Adversary Emulator:** Define a narrow authorized test, snapshot the target, simulate a harmless ATT&CK-mapped behavior, record exact expected events and stop conditions.
2. **Blue Team / Detection Engineer:** Capture Sysmon, Windows Event Logs and network events. Identify which of the expected behaviors were seen, and test a Sigma/SIEM detection against the dataset.
3. **Threat Hunter:** Begin without the simulation answer key, use a hypothesis and identify any suspicious behaviors the alerting system missed; document false positives.
4. **DFIR Analyst:** Reconstruct an evidence-based incident timeline from saved logs and a prepared image; identify missing evidence and confidence levels.
5. **Purple Team:** Close a detection gap or harden a control, repeat the same safe test, and compare coverage, time to detection and false positives.

### Optional extensions
- **CTI:** Derive the scenario from a public advisory and assess source confidence.
- **BAS:** Turn the scenario into a recurring detection regression test.
- **AD security:** Add synthetic domain login and group-policy events.
- **Deception:** Introduce a decoy account or controlled mock service and compare signal quality.
- **Cloud:** Replicate the analytic problem using sample CloudTrail/IAM records.
- **AI tutor:** Ask the local model to teach terms, explain sanitized logs, quiz your reasoning, and evaluate the written report. Do **not** let it run privileged or offensive actions autonomously.

### Required capstone artifacts

- Authorized rules of engagement and sanitized network diagram.
- Baseline, test plan, snapshot/rollback procedure.
- ATT&CK techniques and D3FEND-inspired defensive controls.
- Detection code and tests with false-positive notes.
- Hunt notebook and forensic timeline.
- Before/after Purple Team scorecard.
- README with reproducible steps and redacted screenshots.

**Pass criteria:** The team can reproduce the observations, identify at least one telemetry gap, improve one control or detection, retest and explain the outcome.

## Learning progression and lightweight check-ins

**Stage A — Prerequisites:** AI tutor, Linux/Windows fundamentals, basic network isolation, snapshots and logging.

**Stage B — First investigations (recommended):** A1 Threat Hunting → A3 Detection Engineering → A2 Adversary Emulation → A4 DFIR. These can be alternated rather than completed linearly.

**Stage C — Chosen deep tracks:** A7 Web/API Security (build → test → fix with HTML/JS/PHP/SQL), A10 CTI/OSINT (public research → hunt hypothesis), and ORACLE AI security (prompt-injection/tool-boundary tests). Bring in A6 identity and A12 BAS only when necessary.

**Stage D — Later deep research:** A5 Malware Analysis & Reverse Engineering, deliberately after VM isolation, snapshots, and relevant OS/binary foundations; introduce C, then C++, then Assembly just in time. This is a selected specialization, **not a throwaway elective**.

**Stage E — Breadth and integration:** Short wireless/SDR/embedded working-knowledge demonstrations; one A8 cloud IAM/logging exploration; optional A9/A11 only if useful.

**Stage F — Capstone:** One Red → Blue → Hunt → DFIR → Purple investigation; repeat or extend with web/CTI/AI security scenarios.

**Stage E — Capstone:** One Red → Blue → Hunt → DFIR → Purple investigation; repeat with new scenarios or the separately planned wireless/RF curriculum.

**Per-module reflection questions**
- What surprised me? What was my hypothesis?
- Which observation supports my conclusion? Which would disprove it?
- What could have produced the same event innocently?
- What was prevented, detected or missed?
- How would I improve the system or the next experiment?
- Can I explain the finding without relying on a tool's verdict?

**GitHub reporting format:** `security-lab/<module>/<scenario>/README.md`, redacted diagrams and scripts, a summary of test data, outputs and lessons. Keep personally identifying telemetry and credentials out of the repository.

---

> **Return point:** Maintain ORACLE and the isolated THE FORGE lab as prerequisites; begin hands-on networking/reconnaissance and threat-hunting work when the environment is ready. No fixed study calendar, and no need to master every supporting topic before building.
