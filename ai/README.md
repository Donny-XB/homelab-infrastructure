# Local AI Assistant and Agents

## Next Project — Local Cybersecurity Tutor

**Priority as of 2026-10-14:** Complete the local AI assistant **before** beginning the cybersecurity training labs. NAS and Plex are now operational on the Raspberry Pi 5.

- **Compute target:** Dell OptiPlex 7060, separate from NAS workloads.
- **First check:** Confirm actual CPU, RAM, GPU, and free storage before selecting runtime, quantization, or model.
- **Function:** Private, locally running tutoring assistant for cybersecurity learning, explanations, quizzes, and authorized lab planning; prefer local notes and documentation for retrieval.
- **Architecture:** Start with local chat/RAG; add carefully permissioned tools only if useful, with explicit approval for changes.
- **Offline goal:** After downloading and preparing required software/models, normal tutoring should not require a cloud API.
- **Acceptance test:** An interactive session answers study questions, references local notes, and remains available with outside internet disconnected.


This section tracks AI-agent experiments for the homelab.

## Goals

- Build useful agents that interact with home infrastructure
- Keep agents local-first where practical
- Use read-only access by default
- Require explicit approval for destructive or privileged actions
- Separate credentials and permissions per agent
- Log every action agents take

## Planned Agents

### Infrastructure Agent
Read system health from Proxmox, the NAS, Docker services, and Home Assistant.

### Home Automation Agent
Interact with Home Assistant through allowlisted actions and summarize Ring/Home Assistant events.

### Media Agent
Help manage the currently running Plex library and possible future Jellyfin/Immich metadata, duplicates, and storage growth.

### Privacy Agent
Track privacy tasks without storing sensitive secrets in GitHub.

### Security Analyst Agent
Analyze approved Wazuh, Sysmon, Suricata, and network telemetry.

### Recovery Agent
Assist with backup verification and disaster-recovery exercises.

## Safety Architecture

Agents should never receive unrestricted root or shell access.

Prefer narrowly scoped functions such as:

- get_proxmox_status()
- get_nas_health()
- get_recent_camera_events()
- check_backups()
- start_lab_vm()
- stop_lab_vm()

Any action that deletes data, changes firewall rules, exposes services, changes access control, or modifies security settings should require explicit human approval.

## Future Stack

- Local LLM runtime
- Python agent services
- Home Assistant API
- Proxmox API
- NAS health checks
- Docker API
- Wazuh/Sysmon/Suricata data
- Structured audit logs
