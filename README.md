# 🛡️ MDE Multi-Framework Audit Tracker

**A browser-based Microsoft Defender for Endpoint audit tracker for MSSP security engineers, mapping ~160 tasks across four compliance frameworks — NIST CSF 2.0, Cyber Essentials, SOC 2, and NIST 800-53 — with per-task status, notes, live progress metrics, framework switching, dark/light mode, and CSV, HTML, and JSON export.**

---

## Overview

The MDE Multi-Framework Audit Tracker is a self-contained, single-file HTML dashboard designed for security engineers and analysts at Managed Security Service Providers (MSSPs) operating within the Microsoft Security stack. It provides a structured, auditable, and evidence-ready approach to deploying and validating Microsoft Defender for Endpoint (MDE) configurations against four major compliance and security frameworks simultaneously.

All state is stored locally in the browser via `localStorage`. There is no backend, no authentication layer, no external dependencies beyond Google Fonts, and no data is ever transmitted off-device. The entire tool is a single portable `.html` file — open it in any modern browser and it works immediately.

---

## Framework Coverage

### 🔵 NIST Cybersecurity Framework 2.0 — 57 Tasks

NIST CSF 2.0 is organized around six core functions. Each function maps directly to a phase of MDE deployment and operationalization.

| Function | ID | Tasks | MDE Focus |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory, tagging |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker, Conditional Access |
| Detect | DE | 10 | EDR sensor health, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, escalation matrix, playbooks |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis, quarterly health review |

Every task includes a mapped NIST CSF 2.0 subcategory reference (e.g., `PR.PS-01`, `DE.CM-09`, `RS.MA-04`) for direct traceability to the framework.

---

### 🟢 Cyber Essentials — 29 Tasks

The UK government-backed Cyber Essentials scheme defines five technical controls. All five are mapped to specific MDE, Intune, and Entra ID configurations.

| Control | ID | Tasks | MDE Focus |
|---|---|---|---|
| Firewalls | FW | 6 | Windows Defender Firewall, Network Protection, Web Content Filtering, SmartScreen |
| Secure Configuration | SC | 8 | Security Baselines, Tamper Protection, ASR rules, service hardening, AutoRun |
| User Access Control | UAC | 6 | MFA via Conditional Access, MDE RBAC, Credential Guard, PAW device group |
| Malware Protection | MP | 6 | NGAV cloud protection, MAPS, PUA protection, behavioral monitoring, sensor coverage |
| Patch Management | PU | 5 | TVM vulnerability tracking, Windows Update for Business, EOS software, 14-day SLA |

Cyber Essentials Plus and IASME Cyber Assurance candidates will find this framework particularly useful as pre-assessment validation evidence.

---

### 🟣 SOC 2 — 31 Tasks

SOC 2 Trust Service Criteria (TSC) are organized around the Common Criteria (CC) control families. Tasks map MDE capabilities to the evidence requirements auditors expect.

| Criteria | ID | Tasks | MDE Focus |
|---|---|---|---|
| Control Environment | CC1 | 3 | RBAC documentation, named security officers, published policy |
| Communication & Information | CC2 | 3 | Alert notifications, Sentinel reporting workbook, incident communication |
| Risk Assessment | CC3 | 3 | TVM baseline, risk acceptance criteria, quarterly Secure Score review |
| Monitoring Activities | CC4 | 3 | EDR sensor health monitoring, Sentinel anomaly detection, monthly review |
| Control Activities | CC5 | 3 | ASR policy with exception register, device compliance, change management |
| Logical & Physical Access | CC6 | 5 | MFA for portal, device compliance CA, RBAC reviews, PIM, service account audit |
| System Operations | CC7 | 5 | AIR automation, incident SLAs, Live Response audit, isolation test, config backup |
| Change Management | CC8 | 3 | Version-controlled config baseline, policy approval workflow, audit log review |
| Risk Mitigation | CC9 | 3 | Third-party risk register, data residency/DPA documentation, multi-tenant boundaries |

SOC 2 tasks are explicitly designed to produce audit evidence — each task description references what documentation, logs, or approval records are expected as proof of control operation.

---

### 🟠 NIST 800-53 Rev 5 — 42 Tasks

NIST SP 800-53 Rev 5 provides security and privacy controls for federal and high-assurance environments. Tasks map to eight of the most critical control families relevant to endpoint security.

| Family | ID | Tasks | MDE Focus |
|---|---|---|---|
| Access Control | AC | 5 | MDE RBAC, access reviews, Conditional Access, Live Response controls, mobile device access |
| Audit & Accountability | AU | 5 | Admin audit logs, KQL audit queries, log review process, 12-month retention, event generation |
| Configuration Management | CM | 5 | Baseline config in version control, Security Baselines, ASR enforcement, least functionality, software inventory |
| Identification & Authentication | IA | 4 | Phishing-resistant MFA, PIM activation, service account password policy, certificate-based enrollment |
| Incident Response | IR | 5 | IR plan documentation, AIR and manual workflows, Sentinel IR dashboard, escalation chain, tabletop testing |
| Risk Assessment | RA | 3 | Secure Score/TVM baseline, continuous vulnerability scanning, risk response decisions |
| System & Communications Protection | SC | 4 | Network Protection, WCF/DNS filtering, BitLocker, process isolation via ASR |
| System & Information Integrity | SI | 5 | NGAV cloud protection, patch SLAs, EDR block mode, continuous monitoring, Tamper Protection/WDAC |

---

## Features

### Dashboard Overview
The landing page aggregates all four frameworks into a single view with framework cards showing live completion percentages, task counts by status, and a cross-framework comparison table. This provides an immediate executive-level posture snapshot across all compliance obligations simultaneously.

### Framework Switching
The header navigation bar allows instant switching between the Overview and any of the four frameworks. Each framework has a distinct color identity that propagates through the entire UI — accent colors, progress indicators, task border highlights, the logo icon gradient, and the JSON export button all update to reflect the active framework. This makes it immediately clear which context you are operating in.

### Per-Task Tracking
Every task supports four status states: Not Started, In Progress, Complete, and Blocked. Status can be updated via dropdown selector or by toggling the checkbox. Completed tasks receive a visual strikethrough. A free-text notes field per task supports ticket references, engineer observations, approval evidence links, or blocker descriptions. All state saves automatically to `localStorage` on every interaction.

### Category Navigation
Within each framework, a tab bar provides navigation between control families or functional categories (e.g., GV/ID/PR/DE/RS/RC for CSF, FW/SC/UAC/MP/PU for Cyber Essentials, CC1–CC9 for SOC 2, AC/AU/CM/IA/IR/RA/SC/SI for 800-53). An "All" tab shows all categories stacked for a scrollable full-framework view. Category tabs display live completion counters.

### Live Metrics
The framework header stat row updates in real time as tasks are marked: overall completion percentage, completed count, in-progress count, blocked count, high-priority pending count, and total task count. The Overview page framework cards and comparison table also reflect live state.

### Dark / Light Mode
Full dark and light theme support with a single toggle. Theme preference persists across sessions via `localStorage`. The dark theme uses a deep navy palette suited for SOC environments with low ambient light.

### Export Options
Three export formats are available from the Export button in the header, or via the `{ } JSON` button for a quick config preview:

| Format | Scope | Use Case |
|---|---|---|
| **CSV** | All frameworks | Import into Excel/Sheets for custom reporting, pivot tables, or sharing with non-technical stakeholders |
| **HTML Report** | All frameworks | Standalone printable audit report with framework-colored section headers, task descriptions, status, and notes — ready for client delivery or auditor submission |
| **JSON Config** | Active framework or all | Full structured configuration export for version control, API ingestion, audit evidence archiving, or dashboard state portability |

The JSON modal includes a live preview with one-click copy to clipboard before downloading.

---

## Use Cases

### 1. Multi-Framework Client Onboarding (MSSP)
When a client requires simultaneous compliance against multiple frameworks (e.g., Cyber Essentials for UK compliance plus NIST CSF 2.0 for enterprise risk management), load the dashboard at project start, complete tasks in parallel across frameworks, and export a combined HTML report at project close. The JSON config serves as the deliverable baseline for client handover documentation.

### 2. SOC 2 Type II Audit Preparation
SOC 2 auditors expect evidence of consistent control operation over the audit period. Use the SOC 2 framework to track completion of each CC control, recording ticket numbers and approval evidence in the notes fields. Export the HTML report as a pre-audit self-assessment document. The task descriptions are deliberately written to align with what auditors will test — documentation requirements, approval workflows, quarterly review cadences, and evidence retention.

### 3. Cyber Essentials / Cyber Essentials Plus Assessment
Use the CE framework as a pre-assessment readiness checklist. The five CE controls (Firewalls, Secure Configuration, User Access Control, Malware Protection, Patch Management) are mapped directly to the technical verifications an assessor will perform. Mark items as Complete only when evidence is confirmed. Export the report as a structured readiness pack to share with the certifying body.

### 4. NIST 800-53 FedRAMP / High-Assurance Deployments
For clients in regulated, federal-adjacent, or high-assurance environments, the 800-53 framework provides control-family-level tracking aligned to NIST SP 800-53 Rev 5. Use this framework alongside a System Security Plan (SSP) to document which MDE controls satisfy which 800-53 requirements. Export JSON for integration into GRC platforms.

### 5. Continuous Compliance Monitoring
After initial deployment, maintain the dashboard as a living compliance record. Return to it monthly or quarterly to update task statuses as configurations drift or are updated, mark newly completed remediation actions, log observations from Defender Secure Score reviews, and update notes with evidence references. Export a dated HTML or CSV snapshot before each client review cycle.

### 6. Security Engineer Onboarding & Knowledge Transfer
New engineers joining an MSSP team can use the dashboard as a structured guide to MDE's full capability surface, organized by compliance rationale. Each task description explains the what, where (portal or policy location), and why (compliance control reference). Alongside the README, this provides a complete self-study curriculum for MDE deployment.

### 7. Client Quarterly Business Reviews (QBRs)
Export the HTML report before quarterly client meetings. The per-framework completion percentages, status breakdowns, and color-coded task lists provide a professional, structured audit posture summary that communicates progress clearly to non-technical stakeholders without exposing raw configuration details or internal notes.

### 8. Compliance Gap Assessment on Existing Deployments
For clients with existing MDE deployments, use the dashboard to assess the current state against all four frameworks simultaneously. Walk through each task, mark genuinely complete controls as Complete, mark missing or partially implemented controls as In Progress or Blocked with notes describing the gap. Export the CSV for a formal gap analysis report with prioritized remediation recommendations.

### 9. Incident Response Readiness Review
Focus specifically on the Respond and Recover categories in CSF 2.0, the IR control family in NIST 800-53, and the System Operations controls in SOC 2. Use these as a structured IR readiness checklist: verify AIR automation levels, Live Response configuration, device isolation workflows, escalation matrices, and playbook existence. Mark gaps as Blocked with notes referencing the responsible team or ticket.

### 10. Version-Controlled Compliance Baseline (GitOps)
Export the JSON config at the end of each sprint or deployment phase and commit it to a git repository with a meaningful commit message. Over time, this creates a version history of the compliance posture that can be diffed to show what changed between periods — useful for SOC 2 Type II continuous monitoring evidence, client change management records, and internal audit trails.

---

## Getting Started

1. Download `mde-multi-audit-dashboard.html`
2. Open in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, build tools, or internet connection required after initial load
4. Select a framework from the header switcher or start on the Overview page
5. Update task statuses and notes — all changes save automatically
6. Export at any time using the Export or JSON buttons in the header

---

## Data & Privacy

All task state and preferences are stored exclusively in the browser's `localStorage` under the key `mde-multi-state-v2`. No data is transmitted to any server at any point. The dashboard is fully offline-capable after the initial Google Fonts load. To move state to another machine, export the JSON config and reference it to manually set status on the new device, or copy the `localStorage` value directly via browser developer tools.

---

## Technical Notes

- **Format**: Single self-contained `.html` file — no dependencies, no build step, no server required
- **Fonts**: Syne (headings/brand), JetBrains Mono (code/references/metrics), DM Sans (body/UI) via Google Fonts
- **Storage**: `localStorage` key `mde-multi-state-v2` for task state; `mde-theme` for theme preference
- **Browser support**: Chrome 90+, Edge 90+, Firefox 90+, Safari 15+ (requires `color-mix()` CSS support)
- **File size**: ~87KB uncompressed — loads instantly
- **Export**: Client-side only via `Blob` + object URLs — no server, no upload

---

## Microsoft Security Stack Coverage

All tasks are scoped to the Microsoft Security ecosystem, covering:

| Product | Usage in Dashboard |
|---|---|
| **Microsoft Defender for Endpoint (MDE)** | Core EDR, AIR, Live Response, TVM, device inventory, ASR, NGAV |
| **Microsoft Defender XDR Portal** | Alert management, incident correlation, Advanced Hunting, Threat Analytics |
| **Microsoft Intune** | Endpoint Security policies, Security Baselines, device compliance, WUfB |
| **Microsoft Entra ID** | RBAC, Conditional Access, PIM, Credential Guard, device compliance integration |
| **Microsoft Sentinel** | SIEM/SOAR integration, analytics rules, UEBA, IR dashboards, audit log ingestion |
| **Microsoft Defender Vulnerability Management (TVM)** | Exposure Score, CVE tracking, software inventory, EOS detection |
| **Microsoft Defender for Identity** | Lateral movement detection, deception, identity behavioral analytics |
| **Power Automate** | Automated response flows, ITSM ticket creation, SOC notifications |
| **Windows Defender Application Control (WDAC)** | Application allowlisting for high-risk device groups |

---

## Framework Reference Documents

| Framework | Version | Issuing Body | Primary Audience |
|---|---|---|---|
| NIST Cybersecurity Framework | 2.0 (2024) | NIST | All sectors — risk-based |
| Cyber Essentials | Current scheme | NCSC / IASME (UK) | UK organisations, supply chain |
| SOC 2 | Trust Service Criteria 2017 (updated) | AICPA | SaaS, cloud, service providers |
| NIST SP 800-53 | Revision 5 (2020) | NIST | Federal, high-assurance, FedRAMP |

---

*MDE Multi-Framework Audit Tracker v2.0 | Built for MSSP Security Engineers | Microsoft Security Stack*
