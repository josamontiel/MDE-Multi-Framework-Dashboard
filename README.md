# 🛡️ MDE Multi-Framework Audit Tracker

**A browser-based Microsoft Defender for Endpoint audit tracker for MSSP security engineers, mapping ~153 tasks across four compliance frameworks — NIST CSF 2.0, Cyber Essentials, SOC 2, and NIST 800-53 — with per-task compliance guidance, gap analysis, status tracking, notes, live progress metrics, dark/light mode, mobile support, and CSV, HTML, and JSON export.**

---
<img width="1440" height="726" alt="Screenshot 2026-03-22 at 20 39 41" src="https://github.com/user-attachments/assets/3cf5c942-e4c0-4344-88ba-41a3a86019dd" />

## Overview

The MDE Multi-Framework Audit Tracker is a self-contained, single-file HTML dashboard designed for security engineers and analysts at Managed Security Service Providers (MSSPs) operating within the Microsoft Security stack. It provides a structured, auditable, and evidence-ready approach to deploying and validating Microsoft Defender for Endpoint (MDE) configurations against four major compliance frameworks simultaneously.

Every task includes actionable compliance guidance — the exact portal, navigation path, step-by-step instructions, and where applicable, a PowerShell cmdlet or KQL query — so engineers know precisely what to do, not just what needs doing.

All state is stored locally in the browser via `localStorage`. There is no backend, no authentication layer, no external dependencies beyond Google Fonts, and no data is ever transmitted off-device. The entire tool is a single portable `.html` file — open it in any modern browser and it works immediately.

---

## Framework Coverage

### 🔵 NIST Cybersecurity Framework 2.0 — 57 Tasks

| Function | ID | Tasks | MDE Focus |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory, tagging |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker, Conditional Access |
| Detect | DE | 10 | EDR sensor health, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, escalation matrix, playbooks |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis, quarterly health review |

---

### 🟢 Cyber Essentials — 29 Tasks

| Control | ID | Tasks | MDE Focus |
|---|---|---|---|
| Firewalls | FW | 6 | Windows Defender Firewall, Network Protection, Web Content Filtering, SmartScreen |
| Secure Configuration | SC | 8 | Security Baselines, Tamper Protection, ASR rules, service hardening, AutoRun |
| User Access Control | UAC | 6 | MFA via Conditional Access, MDE RBAC, Credential Guard, PAW device group |
| Malware Protection | MP | 6 | NGAV cloud protection, MAPS, PUA protection, behavioral monitoring, sensor coverage |
| Patch Management | PU | 5 | TVM vulnerability tracking, Windows Update for Business, EOS software, 14-day SLA |

---

### 🟣 SOC 2 — 31 Tasks

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

---

### 🟠 NIST 800-53 Rev 5 — 36 Tasks

| Family | ID | Tasks | MDE Focus |
|---|---|---|---|
| Access Control | AC | 5 | MDE RBAC, access reviews, Conditional Access, Live Response controls, mobile device access |
| Audit & Accountability | AU | 5 | Admin audit logs, KQL audit queries, log review process, 12-month retention, event generation |
| Configuration Management | CM | 5 | Baseline config in version control, Security Baselines, ASR enforcement, least functionality |
| Identification & Authentication | IA | 4 | Phishing-resistant MFA, PIM activation, service account password policy, certificate enrollment |
| Incident Response | IR | 5 | IR plan documentation, AIR workflows, Sentinel IR dashboard, escalation chain, tabletop testing |
| Risk Assessment | RA | 3 | Secure Score/TVM baseline, continuous vulnerability scanning, risk response decisions |
| System & Communications Protection | SC | 4 | Network Protection, WCF/DNS filtering, BitLocker, process isolation via ASR |
| System & Information Integrity | SI | 5 | NGAV cloud protection, patch SLAs, EDR block mode, continuous monitoring, Tamper Protection |

---

## Features

### "How to Comply" — Per-Task Compliance Guidance

Every task has a collapsible **"How to comply →"** panel that expands inline when clicked. Each panel contains three components:

**Portal badge + navigation path** — a colour-coded badge identifies which Microsoft portal or tooling is required, alongside the exact menu trail to the relevant setting:

| Badge | Portal |
|---|---|
| 🔵 Defender Portal | Microsoft Defender XDR portal — alerts, policies, Advanced Hunting, TVM |
| 🟣 Microsoft Intune | Endpoint security policies, Security Baselines, device compliance, disk encryption |
| 🟦 Entra ID | Identity, RBAC, Conditional Access, Privileged Identity Management |
| 🔷 Microsoft Sentinel | SIEM/SOAR, analytics rules, workbooks, data connectors |
| 🟢 PowerShell | On-device verification cmdlets and automation scripts |
| 🟠 M365 Admin | Licensing assignment, tenant-level settings |
| 🟩 Azure Portal | Key Vault, Power Automate flows, Static Web Apps |
| ⬜ Internal Process | Documentation, policy drafting, change management, or GRC platform steps |

**Step-by-step action** — plain-English instructions for exactly what to configure, enable, document, or test to satisfy the control.

**Command / Query block** (59 tasks) — a ready-to-use PowerShell cmdlet or KQL query for verification or automation. Examples include `Get-MpPreference` for AV policy validation, `Get-BitLockerVolume` for encryption status, Advanced Hunting KQL for detection coverage, and Sentinel KQL for audit log queries.

The panel is collapsed by default and operates independently per task — engineers can expand only the controls they are actively working on without affecting others.

<img width="1438" height="820" alt="Screenshot 2026-03-23 at 19 10 29" src="https://github.com/user-attachments/assets/26620b3c-b95a-49ad-889a-69a9ddc0ead0" />


---

### Gap Analysis

The **🔍 Gap Analysis** tab enables engineers to upload a previously exported JSON configuration and compare it against the current tracker state. This surfaces compliance drift, regressions, and improvements between two points in time across all four frameworks simultaneously.

**Uploading a baseline** is done via the **⬆ Import** button in the header. The upload zone supports click-to-browse and drag-and-drop. Files are validated client-side before processing, with clear error messages for incompatible inputs.

Once loaded, the Gap Analysis view classifies every task with a delta type:

| Delta | Meaning |
|---|---|
| ✅ Compliant | Complete in both baseline and current state |
| 📈 Improved | Not complete in baseline, now complete |
| ⚠️ Regression | Was complete in baseline, no longer complete — requires investigation |
| 🔴 Gap | Not complete in either baseline or current — unresolved control |
| 🚫 Blocked | Currently blocked in the active tracker |
| 🟡 In Progress | Work started but not yet finished |
| 🆕 New Control | Task not present in the uploaded baseline |

**Summary metrics** show counts per delta type and an **overall compliance score** — the percentage of controls that are Compliant or Improved.

**Baseline metadata** is surfaced from the uploaded config — export date and covered frameworks — so engineers can confirm they are comparing the correct document.

**Filters** allow drilling into a single delta type across all frameworks simultaneously. Selecting "Regressions" isolates all tasks that were previously complete but are no longer, making remediation prioritisation straightforward.

**Gap exports** — the Gap Analysis view has its own Export CSV and Export HTML Report buttons producing gap-specific outputs with baseline status, current status, and delta classification columns, suitable for client-facing gap reports or audit evidence.

**Clearing** — the ✕ Clear button resets the gap state and returns to the Overview without affecting the current tracker data.

---

### Dashboard Overview

The landing page aggregates all four frameworks into a single view with framework cards showing live completion percentages, task counts by status, and a cross-framework comparison table providing an immediate executive-level posture snapshot.

---

### Framework Switching

The header navigation bar allows instant switching between the Overview, any of the four frameworks, and the Gap Analysis view. Each framework has a distinct colour identity that propagates through the entire UI. When a gap analysis is loaded, the Gap Analysis tab displays a **LIVE** badge.

---

### Per-Task Tracking

Every task supports four status states: Not Started, In Progress, Complete, and Blocked. Status updates via dropdown or checkbox toggle. Completed tasks receive a visual strikethrough. A free-text notes field per task holds ticket references, engineer observations, approval evidence links, or blocker descriptions. All state saves automatically on every interaction.

---

### Category Navigation

Within each framework, a tab bar provides navigation between control families. An "All" tab shows all categories stacked. Category tabs display live completion counters. Tabs scroll horizontally on mobile.

---

### Live Metrics

The framework header stat row updates in real time: completion percentage, completed, in-progress, blocked, high-priority pending, and total. The Overview cards and comparison table reflect live state.

---

### Mobile Friendly

The dashboard is fully responsive across three breakpoints:

**≤900px (tablet)** — framework switcher compresses, comparison table gains horizontal scroll, stat pills wrap.

**≤768px (mobile)** — header reflows to two rows, framework switcher scrolls horizontally. Task rows restack: content on top, full-width status dropdown, full-width notes textarea. Category tabs scroll horizontally. Modals go near full-width.

**≤480px (small mobile)** — logo and brand shrink, Export/JSON button labels hide leaving icons only, font sizes tighten.

---

### Dark / Light Mode

Full dark and light theme support via a single toggle. The dark theme uses a deep navy palette suited for SOC environments with low ambient light. Theme preference persists across sessions.

---

### Export Options

| Format | Scope | Use Case |
|---|---|---|
| **CSV** | All frameworks | Import into Excel or Sheets for custom reporting or stakeholder sharing |
| **HTML Report** | All frameworks | Standalone printable audit report — ready for client delivery or auditor submission |
| **JSON Config** | Active framework or all | Full structured config for version control, gap analysis baseline, or GRC ingestion |
| **Gap CSV** | All frameworks | Gap analysis results with baseline vs. current status and delta classification |
| **Gap HTML Report** | All frameworks | Printable gap analysis report with compliance score, delta breakdown, and per-task comparison |

---

## Use Cases

### 1. New Client MDE Deployment (MSSP)
At project start, export a JSON config as the deployment baseline. Work through tasks using the "How to comply" guidance to configure each control in the right portal. Export the HTML report at project close as a structured deployment evidence pack, and the JSON config as the technical handover baseline.

### 2. Pre-Assessment Gap Analysis
Before a formal audit, upload a client's existing JSON baseline. The gap analysis immediately surfaces regressions (controls that were compliant but have drifted), unresolved gaps, and controls never addressed. Export the gap report as the pre-assessment remediation plan with prioritised actions.

### 3. SOC 2 Type II Continuous Monitoring
Track each CC control over the audit period, recording ticket numbers and approval evidence in notes. Export JSON monthly as point-in-time monitoring evidence. Import the previous month's export to confirm no regressions before the auditor review period ends.

### 4. Cyber Essentials / CE Plus Readiness
Use the CE framework as a pre-assessment readiness checklist. The "How to comply" portal paths and actions map directly to what an assessor will verify. Mark items Complete only when evidence is confirmed. Export the HTML report as a structured readiness pack.

### 5. NIST 800-53 / FedRAMP Deployments
Use the 800-53 framework with the compliance guidance panels and KQL/PowerShell commands to document which MDE configurations satisfy which control requirements. Export JSON for ingestion into a GRC platform alongside the System Security Plan.

### 6. Compliance Regression Tracking After Changes
After a significant platform update or policy change, export the current JSON, apply the changes, then import the pre-change JSON for gap analysis. Any regressions surface immediately with the exact delta type and task identified.

### 7. Client Quarterly Business Reviews (QBRs)
Export the HTML report before quarterly client meetings. Per-framework completion percentages and colour-coded task status provide a professional audit posture summary for non-technical stakeholders.

### 8. Security Engineer Onboarding
New engineers use the dashboard as a structured MDE capability guide. Each task provides the what, the compliance rationale, and via "How to comply" the exact where and how — including PowerShell and KQL blocks for hands-on verification.

### 9. Version-Controlled Compliance Baseline (GitOps)
Export the JSON config after each sprint or deployment phase and commit to a git repository. Import any previous export at any time to generate a gap analysis showing exactly what changed between periods.

### 10. Multi-Framework Simultaneous Audit Tracking
For clients with overlapping compliance obligations (e.g., Cyber Essentials for UK requirements alongside SOC 2 for US customers), track all frameworks in parallel in a single session. The Overview page cross-framework table shows total status at a glance.

---

## Getting Started

1. Download `mde-multi-audit-dashboard.html`
2. Open in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, build tools, login, or internet connection required after initial load
4. Select a framework from the header switcher or start on the Overview page
5. Click any task's **"How to comply →"** button to expand compliance guidance
6. Update task statuses and notes — all changes save automatically
7. Use **⬆ Import** to upload a baseline JSON config for gap analysis
8. Export using the **⬇ Export** or **{ } JSON** buttons in the header

---

## Data & Privacy

All task state, notes, and preferences are stored exclusively in browser `localStorage` under the key `mde-multi-state-v2`. No data is transmitted to any server. The dashboard is fully offline-capable after the initial Google Fonts load. Uploaded baseline files for gap analysis are processed entirely in browser memory and never written to disk or transmitted externally.

To transfer state to another machine, export the JSON config and use it as a reference, or copy the `localStorage` value directly via browser developer tools.

---

## Technical Notes

- **Format**: Single self-contained `.html` file — no dependencies, no build step, no server
- **Size**: ~140KB uncompressed
- **Fonts**: Syne (headings), JetBrains Mono (code/metrics), DM Sans (body/UI) via Google Fonts
- **Storage**: `localStorage` — `mde-multi-state-v2` for task state, `mde-theme` for theme preference
- **Browser support**: Chrome 90+, Edge 90+, Firefox 90+, Safari 15+ (requires `color-mix()` CSS support)
- **Export**: Client-side only via `Blob` + object URLs — no server required
- **Gap analysis**: Runs entirely in browser memory — no upload, no external service

---

## Microsoft Security Stack Coverage

| Product | Role in Dashboard |
|---|---|
| **Microsoft Defender for Endpoint** | Core EDR, AIR, Live Response, TVM, ASR, NGAV — the primary subject of all tasks |
| **Microsoft Defender XDR Portal** | Alert management, incident correlation, Advanced Hunting, Threat Analytics, deception |
| **Microsoft Intune** | Endpoint Security policies, Security Baselines, device compliance, WUfB, disk encryption |
| **Microsoft Entra ID** | RBAC, Conditional Access, PIM, Credential Guard, device compliance signal |
| **Microsoft Sentinel** | SIEM/SOAR, analytics rules, UEBA, IR dashboards, audit log ingestion, workbooks |
| **Defender Vulnerability Management (TVM)** | Exposure Score, CVE tracking, software inventory, EOS detection, remediation requests |
| **Microsoft Defender for Identity** | Lateral movement detection, deception/honeytokens, identity behavioral analytics |
| **Power Automate** | Automated response flows, ITSM ticket creation, SOC Teams/Slack notifications |
| **Azure Key Vault** | Service account credential storage and rotation for MDE API integrations |
| **Windows Defender Application Control** | Application allowlisting for high-risk device groups |

---

## Framework Reference Documents

| Framework | Version | Issuing Body | Primary Audience |
|---|---|---|---|
| NIST Cybersecurity Framework | 2.0 (2024) | NIST | All sectors — risk-based cybersecurity |
| Cyber Essentials | Current scheme | NCSC / IASME (UK) | UK organisations, supply chain compliance |
| SOC 2 | Trust Service Criteria 2017 (updated) | AICPA | SaaS, cloud, and managed service providers |
| NIST SP 800-53 | Revision 5 (2020) | NIST | Federal agencies, FedRAMP, high-assurance environments |

---

*MDE Multi-Framework Audit Tracker v2.1 | Built for MSSP Security Engineers | Microsoft Security Stack*
