# 🛡️ MDE Multi-Framework Audit Tracker

> **Microsoft Defender for Endpoint · MSSP Security Operations**
> A self-contained browser-based audit tracker covering 9 compliance frameworks, ~270 MDE-mapped tasks, per-task compliance guidance, gap analysis, and full export support — no server, no login, no install required.

---

## Table of Contents

1. [Overview](#overview)
2. [Framework Coverage](#framework-coverage)
3. [Feature Reference](#feature-reference)
4. [Use Cases](#use-cases)
5. [Getting Started](#getting-started)
6. [Data & Privacy](#data--privacy)
7. [Technical Notes](#technical-notes)
8. [Microsoft Security Stack Coverage](#microsoft-security-stack-coverage)
9. [Framework Reference Documents](#framework-reference-documents)

---

## Overview

The MDE Multi-Framework Audit Tracker is a single HTML file designed for security engineers and analysts at Managed Security Service Providers (MSSPs) working within the Microsoft Security ecosystem. It provides a structured, evidence-ready approach to deploying and auditing Microsoft Defender for Endpoint (MDE) against nine compliance and risk management frameworks simultaneously.

Every task includes a **"How to comply"** panel containing the exact portal, navigation path, step-by-step action instructions, and — for 63 tasks — a ready-to-use PowerShell cmdlet or KQL query. Engineers know not just *what* needs doing, but precisely *where* and *how* to do it.

The **Gap Analysis** feature allows engineers to upload a previously exported JSON configuration and receive an instant comparison showing what has improved, regressed, or remained unresolved between two points in time.

All data lives in the browser. Nothing is transmitted externally. The entire tool is ~308KB — open it in a browser and it works immediately.

---

## Framework Coverage

### 🔵 NIST CSF 2.0 — 57 Tasks
**NIST Cybersecurity Framework 2.0 (2024)**

| Function | ID | Tasks | MDE Focus |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory, tagging |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker, Conditional Access |
| Detect | DE | 10 | EDR sensor health, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, escalation matrix, playbooks |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis, quarterly health review |

Each task maps to a specific NIST CSF 2.0 subcategory reference (e.g., `PR.PS-01`, `DE.CM-09`, `RS.MA-04`).

---

### 🟢 Cyber Essentials — 29 Tasks
**UK NCSC/IASME Cyber Essentials (Current Scheme)**

| Control | ID | Tasks | MDE Focus |
|---|---|---|---|
| Firewalls | FW | 6 | Windows Defender Firewall, Network Protection, WCF, SmartScreen |
| Secure Configuration | SC | 8 | Security Baselines, Tamper Protection, ASR rules, service hardening |
| User Access Control | UAC | 6 | MFA via Conditional Access, MDE RBAC, Credential Guard, PAW group |
| Malware Protection | MP | 6 | NGAV cloud protection, MAPS, PUA protection, behavioral monitoring |
| Patch Management | PU | 5 | TVM vulnerability tracking, Windows Update for Business, EOS tracking |

---

### 🟩 Cyber Essentials Plus — 35 Tasks
**UK NCSC/IASME Cyber Essentials Plus (Independent Assessment Tier)**

CE+ builds on the base CE controls with tasks oriented specifically around **demonstration, testing, and evidence production** for an independent assessor. Every task includes what to export, what to test live, and what the assessor will verify.

| Category | ID | Tasks | Focus |
|---|---|---|---|
| Vulnerability Scanning | VS | 6 | TVM authenticated scanning, zero critical/high CVEs, scope asset register |
| Malware Protection Testing | MPT | 5 | EICAR test, behavioral block simulation, PUA test, evidence compilation |
| Network Boundary Testing | NBT | 6 | WCF block verification, Network Protection C2 test, external port scan, SmartScreen |
| Access Control Verification | ACV | 6 | Live MFA test, admin/user separation evidence, RBAC scope isolation, PIM audit log |
| Patch Compliance Evidence | PCE | 6 | OS patch currency (14-day SLA), app patch currency, zero EOS software, mobile OS |
| Assessor Readiness | AR | 6 | Evidence pack compilation, pre-assessment walkthrough, scope sign-off, risk acceptance log |

---

### 🟣 SOC 2 — 31 Tasks
**AICPA Trust Service Criteria (2017, updated)**

| Criteria | ID | Tasks | MDE Focus |
|---|---|---|---|
| Control Environment | CC1 | 3 | RBAC documentation, accountability structure, published security policy |
| Communication & Information | CC2 | 3 | Alert notifications, Sentinel workbook, incident communication procedures |
| Risk Assessment | CC3 | 3 | TVM baseline, risk acceptance criteria, quarterly Secure Score review |
| Monitoring Activities | CC4 | 3 | EDR sensor health monitoring, Sentinel anomaly detection, monthly review |
| Control Activities | CC5 | 3 | ASR exception register, device compliance CA policy, change management |
| Logical & Physical Access | CC6 | 5 | MFA for portal, device compliance CA, RBAC access reviews, PIM, service accounts |
| System Operations | CC7 | 5 | AIR automation, incident SLAs, Live Response audit, isolation test, config backup |
| Change Management | CC8 | 3 | Version-controlled baseline, policy approval workflow, admin audit log review |
| Risk Mitigation | CC9 | 3 | Third-party risk register, data residency/DPA documentation, multi-tenant RBAC |

SOC 2 tasks are written specifically to produce audit evidence — each "How to comply" action describes what documentation, logs, or approval records the auditor will expect as proof.

---

### 🟠 NIST 800-53 Rev 5 — 36 Tasks
**NIST SP 800-53 Revision 5 (2020)**

| Family | ID | Tasks | MDE Focus |
|---|---|---|---|
| Access Control | AC | 5 | MDE RBAC, quarterly access reviews, Conditional Access, PIM, mobile device |
| Audit & Accountability | AU | 5 | Admin audit logs, KQL queries, 12-month retention, event generation validation |
| Configuration Management | CM | 5 | Baseline version control, Security Baselines, ASR enforcement, least functionality |
| Identification & Authentication | IA | 4 | Phishing-resistant MFA, PIM JIT, Key Vault credential storage, cert enrollment |
| Incident Response | IR | 5 | IR plan, AIR workflows, Sentinel IR dashboard, escalation chain, tabletop test |
| Risk Assessment | RA | 3 | Secure Score/TVM baseline, continuous scanning, risk response decisions |
| System & Comms Protection | SC | 4 | Network Protection, WCF/DNS filtering, BitLocker, process isolation via ASR |
| System & Info Integrity | SI | 5 | NGAV cloud protection, patch SLAs, EDR block mode, continuous monitoring, Tamper Protection |

---

### 🔴 PCI DSS v4.0 — 40 Tasks
**Payment Card Industry Data Security Standard v4.0**

All tasks are scoped to cardholder data environment (CDE) device groups and include evidence export instructions aligned to what PCI QSAs expect during assessment.

| Category | Req | Tasks | MDE Focus |
|---|---|---|---|
| Network Security Controls | REQ1 | 6 | Host firewall for CDE, Network Protection, WCF, approved services register, quarterly rule review |
| Secure Configurations | REQ2 | 5 | CDE Security Baseline, service hardening, Tamper Protection, ASR, component inventory |
| Malware Protection | REQ5 | 5 | NGAV for CDE, EDR block mode, 100% sensor coverage, anti-tampering, periodic evaluation |
| Vulnerability Management | REQ6 | 5 | TVM authenticated scan, 30-day patch SLA, EOS software, change control documentation |
| Access Control & Authentication | REQ78 | 6 | MFA, CDE-scoped RBAC, PIM, quarterly access review, 90-day inactive account, lockout policy |
| Audit Logging & Monitoring | REQ10 | 5 | Sentinel ingestion, 12-month retention, daily log review, CDE anomaly alerts, log immutability |
| Security Testing | REQ11 | 4 | Quarterly vuln scans, continuous IDS via EDR, Attack Simulator, FIM via Advanced Hunting |
| Incident Response | REQ12 | 4 | PCI IR plan, AIR for CDE, escalation + card brand notification procedure, annual IR test |

---

### 🟣 NIST Zero Trust SP 800-207 — 31 Tasks
**NIST SP 800-207 Zero Trust Architecture**

Organised around the seven ZT pillars. Every task maps a specific MDE or Microsoft Security capability to a zero trust principle.

| Pillar | ID | Tasks | ZT Implementation via MDE |
|---|---|---|---|
| Identity | ZT-ID | 6 | Phishing-resistant MFA, PIM JIT, risk-based CA, MDE-identity risk link, CAE, Defender for Identity |
| Devices | ZT-DEV | 6 | 100% MDE coverage, device health compliance gate, risk score CA threshold, real-time posture evaluation |
| Network | ZT-NET | 6 | Network Protection block mode, device group micro-segmentation, WCF per group, lateral movement ASR |
| Applications | ZT-APP | 4 | Device compliance for app access, CASB integration, app anomaly hunting, WDAC allowlisting |
| Data | ZT-DATA | 4 | BitLocker, device control (USB block), Controlled Folder Access, Purview DLP endpoint enforcement |
| Visibility & Analytics | ZT-VIS | 5 | MDE + Sentinel unified telemetry, ZT posture workbook, threat intelligence, automated ZT playbooks |

---

### 🟤 NIST RMF SP 800-37 Rev 2 — 31 Tasks
**NIST Risk Management Framework SP 800-37 Revision 2**

Covers the full seven-step RMF lifecycle. Tasks are documentation and governance-oriented, linking MDE technical controls to the formal ATO process.

| Step | ID | Tasks | RMF Focus |
|---|---|---|---|
| Prepare | PR | 5 | Risk strategy, AO/ISSO/ISSM roles, system boundary, inherited controls, CM strategy |
| Categorize | CAT | 4 | FIPS 199 impact levels, information type identification, data flow diagram, GRC registration |
| Select | SEL | 4 | 800-53 baseline selection, control tailoring, SSP control table, CM control mapping |
| Implement | IMP | 5 | Technical control deployment, SSP narratives, operational policies, management governance |
| Assess | ASS | 4 | Security Assessment Plan, MDE control testing, Security Assessment Report, POA&M |
| Authorize | AUT | 4 | Authorisation package compilation, risk determination, ATO memo, stakeholder notification |
| Monitor | MON | 5 | Ongoing control monitoring, Secure Score/TVM metrics, AO status reports, change management |

---

### 🤖 NIST AI RMF AI 100-1 — 21 Tasks
**NIST Artificial Intelligence Risk Management Framework (AI 100-1)**

Specifically addresses the AI and ML-powered capabilities within MDE: Automated Investigation & Remediation (AIR), ML-based alert prioritisation, anomaly detection, behavioral threat scoring, TVM risk scoring, and Microsoft Security Copilot.

| Function | ID | Tasks | AI Risk Focus |
|---|---|---|---|
| Govern | AI-GV | 6 | AI governance policy, accountability roles, AI use policy, human oversight thresholds, Copilot governance |
| Map | AI-MAP | 5 | AI feature inventory, automated action impact mapping, FP risk assessment, ML model dependency documentation |
| Measure | AI-MEA | 5 | FP/FN rate tracking, AIR accuracy measurement, model drift monitoring, Copilot quality scoring, KPI dashboard |
| Manage | AI-MAN | 5 | Human-in-the-loop enforcement, AI override escalation path, detection tuning feedback loop, AI incident handling |

---

## Feature Reference

### "How to Comply" — Per-Task Compliance Guidance

Every task has a collapsible **"How to comply →"** panel. Click it to expand. Each panel contains:

**Portal badge** — colour-coded by tool required:

| Badge | Tool | Colour |
|---|---|---|
| Defender Portal | Microsoft Defender XDR portal | 🔵 Blue |
| Microsoft Intune | Endpoint Security policies, Baselines, compliance | 🟣 Purple |
| Entra ID | Identity, RBAC, Conditional Access, PIM | 🟦 Teal |
| Microsoft Sentinel | SIEM/SOAR, analytics rules, workbooks | 🔷 Dark Blue |
| PowerShell | On-device verification and automation | 🟢 Green |
| M365 Admin | Licensing, tenant-level settings | 🟠 Orange |
| Azure Portal | Key Vault, Power Automate, hosting | 🟩 Dark Teal |
| Internal Process | Documentation, policy, GRC, change management | ⬜ Grey |

**Navigation path** — the exact menu trail to the relevant setting (e.g., `Endpoint security → Antivirus → Create policy → Windows`).

**Step-by-step action** — plain-English instructions for exactly what to configure, enable, document, or demonstrate.

**Command / Query block** (63 tasks) — a ready-to-use PowerShell cmdlet or KQL query. Covers AV policy verification, BitLocker status, firewall rule exports, Advanced Hunting queries, Sentinel KQL for audit evidence, and more.

---

### Gap Analysis

Upload a previously exported JSON configuration via the **⬆ Import** button to compare it against the current tracker state across all frameworks simultaneously.

**Delta classification:**

| Delta | Meaning |
|---|---|
| ✅ Compliant | Complete in both baseline and current state |
| 📈 Improved | Not complete in baseline, now complete |
| ⚠️ Regression | Was complete in baseline, no longer complete — investigate |
| 🔴 Gap | Not complete in either — unresolved control |
| 🚫 Blocked | Currently blocked in active tracker |
| 🟡 In Progress | Work started but not finished |
| 🆕 New Control | Task not present in the uploaded baseline |

**Compliance score** — calculated as `(Compliant + Improved) / Total × 100`. Surfaced at the top of the gap view.

**Filters** — drill into a single delta type across all frameworks. "Regressions" isolates every control that was previously passing but is no longer — critical for post-change reviews.

**Gap exports** — dedicated CSV and HTML report exports from the gap view include baseline status, current status, and delta classification columns.

---

### Dashboard Overview

The landing page shows all frameworks as summary cards with live completion percentages, status breakdowns, and a cross-framework comparison table with progress bars.

---

### Framework Switcher

The header navigation bar provides instant switching between the Overview, any of the nine frameworks, and the Gap Analysis view. Each framework has a distinct colour identity that flows through the entire UI. A **LIVE** badge appears on the Gap Analysis tab when a baseline is loaded.

---

### Per-Task Tracking

Each task supports four states: **Not Started**, **In Progress**, **Complete**, **Blocked**. Update via dropdown or checkbox. Completed tasks receive a visual strikethrough. A notes field holds ticket references, evidence links, engineer observations, or blocker descriptions. All state saves automatically to `localStorage`.

---

### Category Navigation

Within each framework, a tab bar navigates between control families. An **All** tab shows every category stacked. Tabs display live completion counters and scroll horizontally on mobile.

---

### Live Metrics

Framework header stat row updates in real time: completion %, completed count, in-progress, blocked, high-priority pending, and total. Overview cards and the comparison table reflect live state.

---

### Mobile Friendly

Three responsive breakpoints:

| Breakpoint | Changes |
|---|---|
| ≤900px (tablet) | Switcher compresses, comparison table scrolls horizontally, stat pills wrap |
| ≤768px (mobile) | Header reflows to two rows, task rows restack to single column, notes and status selectors go full-width, category tabs scroll horizontally, modals go near full-width |
| ≤480px (small mobile) | Logo and brand shrink, Export/JSON/Import labels hide leaving icons, fonts tighten |

---

### Dark / Light Mode

Single toggle in the header. Deep navy dark theme suited for SOC environments. Persists across sessions.

---

### Export Options

| Format | Content | Typical Use |
|---|---|---|
| **CSV** | All frameworks — task ID, name, reference, priority, status, notes | Import into Excel/Sheets for custom reporting |
| **HTML Report** | All frameworks — full audit report with framework-colour section headers | Client delivery, auditor submission, QBR preparation |
| **JSON Config** | Active framework or all — full structured config with metadata and summary stats | Version control, gap analysis baseline, GRC ingestion |
| **Gap CSV** | All frameworks — baseline status, current status, delta classification | Client-facing gap report |
| **Gap HTML Report** | All frameworks — compliance score, delta breakdown, per-task comparison | Audit evidence, pre-assessment remediation plan |

---

### Feedback & Issue Reporting

A **Feedback** button in the header and a link in the footer both point to the GitHub Issues page at [github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues](https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues) for bug reports and feature requests.

---

## Use Cases

### 1. New Client MDE Onboarding (MSSP)
At project start, export a JSON config as the deployment baseline. Work through tasks using the "How to comply" guidance. Export the HTML report at project close as the deployment evidence pack. The JSON config is the technical handover baseline.

### 2. Pre-Assessment Gap Analysis
Upload the client's existing JSON baseline before a formal audit. The gap analysis surfaces regressions (compliant controls that have drifted), unresolved gaps, and controls never addressed. Export the gap report as the pre-assessment remediation plan.

### 3. PCI DSS QSA Assessment Support
Use the PCI DSS framework to track CDE control implementation. "How to comply" panels include PCI-specific evidence exports (filtered to CDE device group, quarterly rule exports, log immutability configuration). Export HTML report as the QSA pre-assessment self-assessment pack.

### 4. CE / CE Plus Certification
Use the CE framework for base control readiness. Switch to CE+ for assessment preparation — every CE+ task describes what to run live, what to export, and what the assessor will verify. Export the HTML report as the assessor evidence pack.

### 5. SOC 2 Type II Continuous Monitoring
Track CC controls with ticket numbers and approval evidence in notes. Export JSON monthly as point-in-time monitoring evidence. Import the previous month's export to confirm no regressions before the auditor review period ends.

### 6. NIST 800-53 / FedRAMP SSP Development
Use the 800-53 framework alongside the "How to comply" guidance and KQL/PowerShell commands to document MDE control implementations in SSP narratives. Export JSON for GRC platform ingestion.

### 7. NIST RMF ATO Lifecycle Management
Work through the seven RMF steps in sequence. Each task maps to a specific RMF deliverable (categorisation document, SSP control table, SAP, SAR, POA&M, ATO memo). Use the dashboard as the primary control implementation tracker feeding into the authorisation package.

### 8. Zero Trust Architecture Programme Tracking
Use the ZT framework to track progress across all six zero trust pillars simultaneously. The Overview comparison table shows ZT pillar completion alongside other framework compliance — useful for organisations pursuing ZT maturity alongside a formal certification.

### 9. AI Risk Management for Automated SOC Tools
Use the AI RMF framework to govern MDE's automated capabilities before expanding AIR automation levels. Tasks cover the full AI risk lifecycle: governance policy, impact mapping, FP rate measurement, and incident handling for incorrect automated actions.

### 10. Compliance Regression Tracking After Changes
After a platform update, policy change, or incident, export the current JSON and import the pre-change export. Any regressions surface immediately with exact delta type and task identified. Export the gap CSV as the change impact assessment.

### 11. Client QBR Preparation
Export the HTML report before quarterly client meetings. Per-framework completion percentages and colour-coded status columns communicate progress to non-technical stakeholders without exposing internal notes or configuration details.

### 12. Security Engineer Onboarding & Training
New engineers use the dashboard as a structured MDE capability guide. Each task provides the compliance rationale, and the "How to comply" panel provides the exact portal navigation, configuration steps, and verification commands — a complete self-study curriculum covering nine compliance frameworks.

### 13. GitOps Compliance Versioning
Export JSON after each sprint and commit to a git repository. Import any previous export at any time for gap analysis. Over multiple sprints this creates a full version history of compliance posture changes — useful for SOC 2 Type II continuous monitoring evidence and client audit trails.

### 14. Multi-Framework Simultaneous Audit
For clients with overlapping obligations (e.g., PCI DSS + Cyber Essentials + SOC 2), track all frameworks in parallel in a single session. The Overview cross-framework table shows all compliance obligations at a glance and highlights where gaps are concentrated.

---

## Getting Started

1. Download `mde-multi-audit-dashboard.html`
2. Open in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, build tools, login, or internet connection required after initial load
4. Use the **Overview** page for a cross-framework status summary
5. Select a framework from the header switcher
6. Click any task's **"How to comply →"** button to expand compliance guidance
7. Update task statuses and notes — all changes save automatically
8. Use **⬆ Import** to upload a baseline JSON for gap analysis
9. Use **⬇ Export** or **{ } JSON** to export data or configuration

---

## Data & Privacy

All task state, notes, and preferences are stored exclusively in browser `localStorage` under the key `mde-multi-state-v2`. Nothing is transmitted to any external server at any point. The dashboard is fully offline-capable after the initial Google Fonts load. Uploaded baseline files for gap analysis are processed entirely in browser memory and never written to disk or transmitted externally.

To transfer state to another machine, export the JSON config and use it as a reference, or copy the `localStorage` value directly via browser developer tools (`Application → Local Storage`).

---

## Technical Notes

| Property | Detail |
|---|---|
| **Format** | Single self-contained `.html` file |
| **File size** | ~308KB uncompressed |
| **Frameworks** | 9 |
| **Total tasks** | ~270 |
| **Tasks with PowerShell/KQL** | 63 |
| **Fonts** | Syne (headings), JetBrains Mono (code/metrics), DM Sans (UI) via Google Fonts |
| **State storage** | `localStorage` — key `mde-multi-state-v2` (tasks), `mde-theme` (theme) |
| **Browser support** | Chrome 90+, Edge 90+, Firefox 90+, Safari 15+ (requires `color-mix()` CSS) |
| **Export method** | Client-side `Blob` + object URLs — no server required |
| **Gap analysis** | Runs entirely in browser memory — no upload, no external service |
| **Dependencies** | None (Google Fonts only, optional) |

---

## Microsoft Security Stack Coverage

| Product | Role in Dashboard |
|---|---|
| **Microsoft Defender for Endpoint** | Core EDR, AIR, Live Response, TVM, ASR, NGAV — primary subject of all tasks |
| **Microsoft Defender XDR Portal** | Alert management, incident correlation, Advanced Hunting, Threat Analytics, deception |
| **Microsoft Intune** | Endpoint Security policies, Security Baselines, device compliance, WUfB, disk encryption |
| **Microsoft Entra ID** | RBAC, Conditional Access, PIM, Credential Guard, CAE, device compliance signal |
| **Microsoft Sentinel** | SIEM/SOAR, analytics rules, UEBA, IR dashboards, audit log ingestion, workbooks |
| **Defender Vulnerability Management (TVM)** | Exposure Score, CVE tracking, software inventory, EOS detection, remediation requests |
| **Microsoft Defender for Identity** | Lateral movement detection, honeytokens, identity behavioral analytics |
| **Microsoft Defender for Cloud Apps** | Shadow IT discovery, CASB policy, unsanctioned app blocking |
| **Microsoft Purview** | DLP endpoint enforcement, sensitivity label integration |
| **Microsoft Security Copilot** | AI-assisted investigation, incident summarisation (AI RMF governance tasks) |
| **Power Automate / Logic Apps** | Automated response flows, ITSM ticket creation, SOC notifications, Sentinel playbooks |
| **Azure Key Vault** | Service account credential storage and 90-day rotation for MDE API integrations |
| **Windows Defender Application Control** | Application allowlisting for PAW, CDE, and high-risk device groups |
| **Windows Defender Firewall** | Host-based NSC enforced via Intune Endpoint Security — PCI REQ1, CE FW, ZT Network |

---

## Framework Reference Documents

| Framework | Version | Issuing Body | Primary Audience |
|---|---|---|---|
| NIST Cybersecurity Framework | 2.0 (February 2024) | NIST | All sectors — risk-based cybersecurity governance |
| Cyber Essentials | Current scheme | NCSC / IASME (UK) | UK organisations, supply chain compliance |
| Cyber Essentials Plus | Current scheme | NCSC / IASME (UK) | UK organisations requiring independent technical verification |
| SOC 2 | Trust Service Criteria 2017 (updated) | AICPA | SaaS, cloud, and managed service providers |
| NIST SP 800-53 | Revision 5 (September 2020) | NIST | Federal agencies, FedRAMP, high-assurance environments |
| PCI DSS | Version 4.0 (March 2022) | PCI Security Standards Council | Any organisation processing, storing, or transmitting payment card data |
| NIST SP 800-207 | Zero Trust Architecture (August 2020) | NIST | Organisations implementing zero trust network architecture |
| NIST SP 800-37 | RMF Revision 2 (December 2018) | NIST | Federal agencies and organisations pursuing ATO |
| NIST AI 100-1 | AI RMF (January 2023) | NIST | Organisations developing, deploying, or procuring AI systems |

---

## Changelog

### v3.0
- Added **PCI DSS v4.0** — 40 tasks across 8 requirement areas (REQ1, REQ2, REQ5, REQ6, REQ78, REQ10, REQ11, REQ12)
- Added **NIST Zero Trust SP 800-207** — 31 tasks across 6 ZT pillars (Identity, Devices, Network, Applications, Data, Visibility)
- Added **NIST RMF SP 800-37 Rev 2** — 31 tasks across 7 RMF lifecycle steps (Prepare through Monitor)
- Added **NIST AI RMF AI 100-1** — 21 tasks across 4 AI RMF functions (Govern, Map, Measure, Manage)
- Total frameworks: 9 | Total tasks: ~270 | Tasks with PowerShell/KQL: 63

### v2.1
- Added **Cyber Essentials Plus** — 35 tasks across 6 assessment categories
- Fixed "How to comply" toggle (duplicate ID bug resolved via DOM traversal)
- Added mobile-responsive layout (3 breakpoints)
- Added GitHub Issues feedback link in header and footer

### v2.0
- Added **Gap Analysis** feature — upload baseline JSON, compare delta, filter by type, export gap reports
- Added **"How to comply"** panels on all tasks — portal badge, navigation path, action, PowerShell/KQL blocks
- Added **Import** button with drag-and-drop file upload and validation

### v1.0
- Initial release with NIST CSF 2.0, Cyber Essentials, SOC 2, NIST 800-53
- Per-task status tracking, notes, dark/light mode, CSV/HTML/JSON export

---

*MDE Multi-Framework Audit Tracker v3.0 · Built for MSSP Security Engineers · Microsoft Security Stack*
*Feedback & feature requests: [github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues](https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues)*
