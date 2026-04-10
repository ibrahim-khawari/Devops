# Infrastructure CI/CD Setup – Full Session Log

This file contains the full conversational log of the step‑by‑step setup and troubleshooting of an on‑prem Azure DevOps self‑hosted agent, DNS issues, and enterprise CI/CD bootstrapping.

---

## Key Topics Covered
- CI/CD concepts for on‑prem infrastructure
- Azure DevOps private project setup
- PowerShell CI pipeline creation
- Self‑hosted agent installation (Windows Server 2019)
- Service account creation and permissions
- Azure DevOps PAT scopes
- Agent registration process
- Firewall and DNS troubleshooting
- Conditional forwarders and root hints
- Enterprise DNS limitations
- Supported workaround approaches (proxy / hosts file)

---

## Notes
- This document is intended for internal reference and knowledge sharing.
- Sensitive tokens, passwords, and secrets are NOT included.
- Commands shown were executed in controlled environments.

---

## Conversation Export

(The remainder of this document is a redacted but faithful markdown‑formatted reconstruction of the full chat flow. You may extend or split sections as needed.)

---

### CI/CD on‑Prem Planning
We discussed how CI/CD applies to on‑prem infrastructure using:
- Azure DevOps
- PowerShell / PowerCLI
- VMware
- Meraki / SonicWall APIs
- Git as source of truth

Initial phases focused on:
- Script validation
- Read‑only audits
- Low‑risk automation

---

### Azure DevOps Project & Repo Setup
- Private project created
- Repo: `infra-powershell-ops`
- Initial audit script committed
- YAML pipeline for syntax validation

---

### Pipeline Debugging
- YAML indentation issues resolved
- PowerShell parser validation fixed
- Hosted agent limitations identified
- Decision made to move to self‑hosted agent

---

### Self‑Hosted Agent Setup (Infra‑Jay)
- Windows Server 2019 Standard
- Domain‑joined
- Service account: `svc-azdo-agent`
- Local admin rights assigned

---

### Agent Download & Install
- CDN blocked in environment
- Manual GitHub download used
- Agent extracted to `C:zdo-agent`

---

### PAT Creation
- Scope: Agent Pools (Read & manage only)
- Least privilege confirmed

---

### Agent Registration Failure
- Timeouts during `config.cmd`
- Connectivity tests succeeded to dev.azure.com
- AzureEdge CDN DNS resolution failed

---

### DNS Investigation
- Conditional forwarder existed but broken
- Azure internal DNS IP unreachable
- Root hints / recursion issues
- Enterprise DNS restrictions confirmed

---

### Final Outcome
- Determined DNS could not be fixed short‑term
- Proxy not available
- Supported interim solutions identified:
  - HOSTS file workaround (PoC)
  - Alternate subnet / server

---

## End of Export
