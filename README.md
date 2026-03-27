# MDE Multi-Framework Audit Tracker

A self-contained browser-based audit tracker for MSSP security engineers. Covers 9 compliance frameworks, approximately 270 Microsoft Defender for Endpoint-mapped tasks, per-task compliance guidance with portal navigation paths and PowerShell/KQL commands, gap analysis, stakeholder reporting, and full export support. No server, no login, no installation required.
<img width="796" height="655" alt="Screenshot 2026-03-27 at 20 56 31" src="https://github.com/user-attachments/assets/a85d4043-97cb-4c68-81b3-635a90368ba3" />

---

## Table of Contents

1. [Overview](#overview)
2. [Framework Coverage](#framework-coverage)
3. [Feature Reference](#feature-reference)
4. [Use Cases](#use-cases)
5. [Getting Started](#getting-started)
6. [Data and Privacy](#data-and-privacy)
7. [Technical Notes](#technical-notes)
8. [Microsoft Security Stack Coverage](#microsoft-security-stack-coverage)
9. [Framework Reference Documents](#framework-reference-documents)
10. [Changelog](#changelog)

---

## Overview

The MDE Multi-Framework Audit Tracker is a single HTML file designed for security engineers and analysts at Managed Security Service Providers working within the Microsoft Security ecosystem. It provides a structured, evidence-ready approach to deploying and auditing Microsoft Defender for Endpoint against nine compliance and risk management frameworks simultaneously.

Every task includes a "How to comply" panel containing the exact portal, navigation path, step-by-step action instructions, and for 63 tasks a ready-to-use PowerShell cmdlet or KQL query. Engineers know not just what needs doing, but precisely where and how to do it.

The Gap Analysis feature allows engineers to upload a previously exported JSON configuration and receive an instant comparison showing what has improved, regressed, or remained unresolved between two points in time.

The Stakeholder Report generates a plain-language executive summary scoped to the active framework, exportable directly to PDF via the browser's native print dialog.

All data lives in the browser. Nothing is transmitted externally. The entire tool is approximately 300KB — open it in a browser and it works immediately.

---

## Framework Coverage

### NIST CSF 2.0 — 57 Tasks
NIST Cybersecurity Framework 2.0 (February 2024)

| Function | ID | Tasks | MDE Focus |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory, tagging |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker, Conditional Access |
| Detect | DE | 10 | EDR sensor health, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, escalation matrix, playbooks |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis, quarterly health review |

Each task maps to a specific NIST CSF 2.0 subcategory reference (e.g., PR.PS-01, DE.CM-09, RS.MA-04).

---

### Cyber Essentials — 29 Tasks
UK NCSC/IASME Cyber Essentials (Current Scheme)

| Control | ID | Tasks | MDE Focus |
|---|---|---|---|
| Firewalls | FW | 6 | Windows Defender Firewall, Network Protection, WCF, SmartScreen |
| Secure Configuration | SC | 8 | Security Baselines, Tamper Protection, ASR rules, service hardening |
| User Access Control | UAC | 6 | MFA via Conditional Access, MDE RBAC, Credential Guard, PAW group |
| Malware Protection | MP | 6 | NGAV cloud protection, MAPS, PUA protection, behavioral monitoring |
| Patch Management | PU | 5 | TVM vulnerability tracking, Windows Update for Business, EOS tracking |

---

### Cyber Essentials Plus — 35 Tasks
UK NCSC/IASME Cyber Essentials Plus (Independent Assessment Tier)

CE+ builds on the base CE controls with tasks oriented specifically around demonstration, testing, and evidence production for an independent assessor. Every task specifies what to export, what to test live, and what the assessor will verify.

| Category | ID | Tasks | Focus |
|---|---|---|---|
| Vulnerability Scanning | VS | 6 | TVM authenticated scanning, zero critical/high CVEs, scope asset register |
| Malware Protection Testing | MPT | 5 | EICAR test, behavioral block simulation, PUA test, evidence compilation |
| Network Boundary Testing | NBT | 6 | WCF block verification, Network Protection C2 test, external port scan |
| Access Control Verification | ACV | 6 | Live MFA test, admin/user separation evidence, RBAC scope isolation, PIM audit |
| Patch Compliance Evidence | PCE | 6 | OS patch currency (14-day SLA), app patch currency, zero EOS software |
| Assessor Readiness | AR | 6 | Evidence pack compilation, pre-assessment walkthrough, scope sign-off |

---

### SOC 2 — 31 Tasks
AICPA Trust Service Criteria (2017, updated)

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

---

### NIST 800-53 Rev 5 — 36 Tasks
NIST SP 800-53 Revision 5 (September 2020)

| Family | ID | Tasks | MDE Focus |
|---|---|---|---|
| Access Control | AC | 5 | MDE RBAC, quarterly access reviews, Conditional Access, PIM, mobile device |
| Audit & Accountability | AU | 5 | Admin audit logs, KQL queries, 12-month retention, event generation validation |
| Configuration Management | CM | 5 | Baseline version control, Security Baselines, ASR enforcement, least functionality |
| Identification & Authentication | IA | 4 | Phishing-resistant MFA, PIM JIT, Key Vault credential storage, cert enrollment |
| Incident Response | IR | 5 | IR plan, AIR workflows, Sentinel IR dashboard, escalation chain, tabletop test |
| Risk Assessment | RA | 3 | Secure Score/TVM baseline, continuous scanning, risk response decisions |
| System & Communications Protection | SC | 4 | Network Protection, WCF/DNS filtering, BitLocker, process isolation via ASR |
| System & Information Integrity | SI | 5 | NGAV cloud protection, patch SLAs, EDR block mode, continuous monitoring |

---

### PCI DSS v4.0 — 40 Tasks
Payment Card Industry Data Security Standard v4.0

All tasks are scoped to cardholder data environment (CDE) device groups and include evidence export instructions aligned to QSA assessment requirements.

| Category | Req | Tasks | MDE Focus |
|---|---|---|---|
| Network Security Controls | REQ1 | 6 | Host firewall for CDE, Network Protection, WCF, approved services register |
| Secure Configurations | REQ2 | 5 | CDE Security Baseline, service hardening, Tamper Protection, ASR, component inventory |
| Malware Protection | REQ5 | 5 | NGAV for CDE, EDR block mode, 100% sensor coverage, anti-tampering, periodic evaluation |
| Vulnerability Management | REQ6 | 5 | TVM authenticated scan, 30-day patch SLA, EOS software, change control |
| Access Control & Authentication | REQ78 | 6 | MFA, CDE-scoped RBAC, PIM, quarterly access review, lockout policy |
| Audit Logging & Monitoring | REQ10 | 5 | Sentinel ingestion, 12-month retention, daily log review, log immutability |
| Security Testing | REQ11 | 4 | Quarterly vuln scans, continuous IDS via EDR, Attack Simulator, FIM |
| Incident Response | REQ12 | 4 | PCI IR plan, AIR for CDE, escalation and card brand notification, annual IR test |

---

### NIST Zero Trust SP 800-207 — 31 Tasks
NIST SP 800-207 Zero Trust Architecture (August 2020)

| Pillar | ID | Tasks | ZT Implementation via MDE |
|---|---|---|---|
| Identity | ZT-ID | 6 | Phishing-resistant MFA, PIM JIT, risk-based CA, device-identity risk link, CAE |
| Devices | ZT-DEV | 6 | 100% MDE coverage, device health compliance gate, risk score CA threshold |
| Network | ZT-NET | 6 | Network Protection block mode, device group micro-segmentation, lateral movement ASR |
| Applications | ZT-APP | 4 | Device compliance for app access, CASB integration, WDAC allowlisting |
| Data | ZT-DATA | 4 | BitLocker, device control (USB block), Controlled Folder Access, Purview DLP |
| Visibility & Analytics | ZT-VIS | 5 | MDE + Sentinel unified telemetry, ZT posture workbook, automated ZT playbooks |

---

### NIST RMF SP 800-37 Rev 2 — 31 Tasks
NIST Risk Management Framework SP 800-37 Revision 2 (December 2018)

| Step | ID | Tasks | RMF Focus |
|---|---|---|---|
| Prepare | PR | 5 | Risk strategy, AO/ISSO/ISSM roles, system boundary, inherited controls, CM strategy |
| Categorize | CAT | 4 | FIPS 199 impact levels, information type identification, data flow diagram |
| Select | SEL | 4 | 800-53 baseline selection, control tailoring, SSP control table |
| Implement | IMP | 5 | Technical control deployment, SSP narratives, operational policies |
| Assess | ASS | 4 | Security Assessment Plan, MDE control testing, SAR, POA&M |
| Authorize | AUT | 4 | Authorisation package compilation, risk determination, ATO memo |
| Monitor | MON | 5 | Ongoing control monitoring, Secure Score/TVM metrics, AO status reports |

---

### NIST AI RMF AI 100-1 — 21 Tasks
NIST Artificial Intelligence Risk Management Framework (January 2023)

Specifically addresses AI and ML-powered capabilities within MDE: Automated Investigation and Remediation, ML-based alert prioritisation, anomaly detection, behavioral threat scoring, and Microsoft Security Copilot.

| Function | ID | Tasks | AI Risk Focus |
|---|---|---|---|
| Govern | AI-GV | 6 | AI governance policy, accountability roles, AI use policy, human oversight thresholds |
| Map | AI-MAP | 5 | AI feature inventory, automated action impact mapping, FP risk assessment |
| Measure | AI-MEA | 5 | FP/FN rate tracking, AIR accuracy measurement, model drift monitoring |
| Manage | AI-MAN | 5 | Human-in-the-loop enforcement, AI override escalation, detection tuning feedback loop |

---

## Feature Reference

### How to Comply — Per-Task Compliance Guidance

Every task has a collapsible "How to comply" panel. Click it to expand. Each panel contains three components.

**Portal badge and navigation path** — a colour-coded badge identifies which Microsoft portal or tooling is required, alongside the exact menu trail to the relevant setting.

| Badge | Tool |
|---|---|
| Defender Portal | Microsoft Defender XDR portal — alerts, policies, Advanced Hunting, TVM |
| Microsoft Intune | Endpoint security policies, Security Baselines, device compliance, disk encryption |
| Entra ID | Identity, RBAC, Conditional Access, Privileged Identity Management |
| Microsoft Sentinel | SIEM/SOAR, analytics rules, workbooks, data connectors |
| PowerShell | On-device verification cmdlets and automation scripts |
| M365 Admin | Licensing assignment, tenant-level settings |
| Azure Portal | Key Vault, Power Automate flows |
| Internal Process | Documentation, policy drafting, change management, GRC platform steps |

**Step-by-step action** — plain-English instructions for exactly what to configure, enable, document, or test to satisfy the control.

**Command and Query block** (63 tasks) — a ready-to-use PowerShell cmdlet or KQL query for verification or automation. Examples include Get-MpPreference for AV policy validation, Get-BitLockerVolume for encryption status, Advanced Hunting KQL for detection coverage, and Sentinel KQL for audit log queries.

The panel is collapsed by default and operates independently per task.

---

### Gap Analysis

The Gap Analysis tab allows engineers to upload a previously exported JSON configuration and compare it against the current tracker state across all frameworks simultaneously.

Upload a baseline via the Import button in the Actions dropdown. The upload zone supports click-to-browse and drag-and-drop. Files are validated client-side before processing.

Once loaded, every task is classified with a delta type:

| Delta | Meaning |
|---|---|
| Compliant | Complete in both baseline and current state |
| Improved | Not complete in baseline, now complete |
| Regression | Was complete in baseline, no longer complete — requires investigation |
| Gap | Not complete in either baseline or current — unresolved control |
| Blocked | Currently blocked in the active tracker |
| In Progress | Work started but not yet finished |
| New Control | Task not present in the uploaded baseline |

**Summary metrics** show counts per delta type and an overall compliance score — the percentage of controls that are Compliant or Improved.

**Filters** allow drilling into a single delta type across all frameworks simultaneously.

**Gap exports** — the Gap Analysis view has its own Export CSV and Export HTML Report buttons producing gap-specific outputs with baseline status, current status, and delta classification columns.

---

### Stakeholder Report

Each framework view includes a Stakeholder Report button in the top-right of the framework header. This generates a non-technical, plain-language report scoped to the active framework.

The report is built in real time from the current tracker state and contains four sections:

**Executive Summary** — a narrative paragraph describing the overall posture, number of controls completed, in progress, and blocked, and whether any high-priority gaps remain. Language is written for a non-technical audience.

**Framework Status** — a card grid showing each framework (or the single active framework) with a completion bar, percentage, control count, and plain-status label (On Track, In Progress, Getting Started).

**Risk Indicators** — auto-generated from live data. Surfaces blocked controls, incomplete high-priority tasks, and frameworks at low coverage — each with a colour-coded severity badge.

**Recommended Next Steps** — identifies the lowest-progress areas and names the next specific high-priority task within each, giving the reader a concrete action rather than vague guidance.

**Export as PDF** — opens a print-optimised version of the report in a new browser tab and immediately triggers the native print dialog. Select "Save as PDF" as the destination. The report uses an A4 page layout with proper section breaks, white background, and forced colour rendering for accurate PDF output. No external libraries or server required. If the browser blocks the pop-up, a notification prompts the user to allow pop-ups and try again.

The Stakeholder Report is only accessible from within a framework view and is not available on the Overview page.

---

### Dashboard Overview

The landing page aggregates all nine frameworks into a single view. Framework cards show live completion percentages and status breakdowns. The comparison section lists every framework as a row with a progress bar, completion count, and status stats — replacing the previous table layout that required horizontal scrolling. The comparison section is fully responsive at all screen sizes.

---

### Navigation — Three Dropdown Controls

**Framework switcher** — the primary navigation control in the header. Shows the active framework name with a colour dot. Opens a dropdown grouped into Dashboard (Overview, Gap Analysis) and Frameworks (all nine). Each framework item shows a live done/total task counter. Selecting a framework closes the dropdown and switches the view.

**Actions dropdown** — the secondary control in the header. Groups all utility actions into three sections: Data (Import Config, Export, JSON Config), Appearance (Dark/Light theme toggle pill), and Links (Report Issue / Feature on GitHub).

**Category dropdown** — appears within each framework view. Shows the active category name and a live completion count. Opens a list of all categories for that framework, each showing a short description, done/total count, and a mini progress bar. Defaults to "All Controls" on first view. Selecting a category closes the dropdown and shows that section.

Opening any dropdown automatically closes the others to prevent overlap.

---

### Per-Task Tracking

Each task supports four states: Not Started, In Progress, Complete, Blocked. Update via dropdown or checkbox. Completed tasks receive a visual strikethrough. A notes field holds ticket references, evidence links, engineer observations, or blocker descriptions. All state saves automatically to localStorage on every interaction.

---

### Mobile Friendly

Three responsive breakpoints ensure the dashboard works at any screen size.

At 900px and below, the comparison section stays readable with no horizontal scroll. Framework stat pills wrap naturally.

At 768px and below, the header reflows to a single row with the two dropdowns. Task rows restack from a multi-column grid to a single-column layout with full-width status dropdowns and notes fields. Category navigation is naturally compact as a dropdown.

At 480px and below, logo and brand text shrink, font sizes tighten throughout.

---

### Dark and Light Mode

Single toggle in the Actions dropdown using a pill control. The dark theme uses a deep navy palette suited for SOC environments with low ambient light. The light theme is clean and high-contrast. Theme preference persists across sessions.

---

### Export Options

| Format | Content | Typical Use |
|---|---|---|
| CSV | All frameworks — task ID, name, reference, priority, status, notes | Import into Excel or Sheets for custom reporting |
| HTML Report | All frameworks — full audit report with coloured section headers | Client delivery, auditor submission |
| JSON Config | Active framework or all — structured config with metadata and summary stats | Version control, gap analysis baseline, GRC ingestion |
| Gap CSV | All frameworks — baseline status, current status, delta classification | Client-facing gap report |
| Gap HTML Report | All frameworks — compliance score, delta breakdown, per-task comparison | Pre-assessment remediation plan |
| Stakeholder PDF | Active framework — executive summary, framework status, risks, next steps | Client QBRs, CISO briefings, board reporting |

---

### Feedback and Issue Reporting

A Feedback link in the Actions dropdown and a link in the footer both point to the GitHub Issues page for bug reports and feature requests.

Repository: https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues

---

## Use Cases

### 1. New Client MDE Onboarding (MSSP)
At project start, export a JSON config as the deployment baseline. Work through tasks using the "How to comply" guidance. Export the HTML report at project close as the deployment evidence pack. The JSON config is the technical handover baseline. Use the Stakeholder Report to brief the client's security leadership at project end.

### 2. Pre-Assessment Gap Analysis
Upload the client's existing JSON baseline before a formal audit. The gap analysis immediately surfaces regressions (controls that have drifted from compliant), unresolved gaps, and controls never addressed. Export the gap report as the pre-assessment remediation plan.

### 3. PCI DSS QSA Assessment Support
Use the PCI DSS framework to track CDE control implementation. "How to comply" panels include PCI-specific evidence exports filtered to the CDE device group. Export the Stakeholder Report as a PDF for the client's finance and compliance team before the QSA assessment.

### 4. Cyber Essentials and CE Plus Certification
Use the CE framework for base control readiness. Switch to CE+ for assessment preparation — every task describes what to run live, what to export, and what the assessor will verify.

### 5. SOC 2 Type II Continuous Monitoring
Track CC controls with ticket numbers and approval evidence in notes. Export JSON monthly as point-in-time monitoring evidence. Import the previous month's export to confirm no regressions before the auditor review period ends.

### 6. NIST 800-53 and FedRAMP SSP Development
Use the 800-53 framework alongside the "How to comply" guidance and KQL/PowerShell commands to document MDE control implementations in SSP narratives. Export JSON for GRC platform ingestion.

### 7. NIST RMF ATO Lifecycle Management
Work through the seven RMF steps in sequence. Each task maps to a specific RMF deliverable — categorisation document, SSP control table, SAP, SAR, POA&M, ATO memo. Use the dashboard as the primary control implementation tracker feeding into the authorisation package.

### 8. Zero Trust Architecture Programme Tracking
Use the ZT framework to track progress across all six zero trust pillars simultaneously. The Overview comparison section shows ZT pillar completion alongside other framework compliance.

### 9. AI Risk Management for Automated SOC Tools
Use the AI RMF framework to govern MDE's automated capabilities before expanding AIR automation levels. Tasks cover the full AI risk lifecycle: governance policy, impact mapping, FP rate measurement, and incident handling for incorrect automated actions.

### 10. Compliance Regression Tracking After Changes
After a platform update, policy change, or incident, export the current JSON and import the pre-change export. Any regressions surface immediately with exact delta type and task identified.

### 11. Client QBR Preparation
Open the target framework, click Stakeholder Report, and export as PDF. The plain-language executive summary, framework completion percentage, risk indicators, and recommended next steps give the client's leadership team a complete picture without requiring technical context.

### 12. Security Engineer Onboarding and Training
New engineers use the dashboard as a structured MDE capability guide. Each task provides the compliance rationale, and the "How to comply" panel provides the exact portal navigation, configuration steps, and verification commands.

### 13. GitOps Compliance Versioning
Export JSON after each sprint and commit to a git repository. Import any previous export at any time for gap analysis. This creates a full version history of compliance posture changes suitable for SOC 2 continuous monitoring evidence and client audit trails.

### 14. Multi-Framework Simultaneous Audit
For clients with overlapping obligations — PCI DSS, Cyber Essentials, and SOC 2 simultaneously — track all frameworks in parallel in a single session. The Overview comparison section shows all compliance obligations at a glance.

---

## Getting Started

1. Download `mde-multi-audit-dashboard.html`
2. Open in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, build tools, login, or internet connection required after initial load
4. Use the Overview page for a cross-framework status summary
5. Select a framework from the header framework switcher
6. Click any task's "How to comply" button to expand compliance guidance
7. Update task statuses and notes — all changes save automatically
8. Use the Actions dropdown to Import a baseline JSON for gap analysis, Export data, or toggle the theme
9. Open any framework and click Stakeholder Report to generate a PDF-ready executive summary

---

## Data and Privacy

All task state, notes, and preferences are stored exclusively in browser localStorage under the key `mde-multi-state-v2`. Nothing is transmitted to any external server. The dashboard is fully offline-capable after the initial Google Fonts load.

Uploaded baseline files for gap analysis are processed entirely in browser memory and never written to disk or transmitted externally.

The Stakeholder Report PDF is generated client-side by opening a new browser window and triggering the browser's print dialog. No data leaves the device.

To transfer state to another machine, export the JSON config and reference it manually, or copy the localStorage value directly via browser developer tools under Application > Local Storage.

---

## Technical Notes

| Property | Detail |
|---|---|
| Format | Single self-contained .html file |
| File size | Approximately 300KB uncompressed |
| Frameworks | 9 |
| Total tasks | Approximately 270 |
| Tasks with PowerShell or KQL | 63 |
| Fonts | Syne (headings), JetBrains Mono (code/metrics), DM Sans (UI) via Google Fonts |
| State storage | localStorage — key mde-multi-state-v2 (tasks), mde-theme (theme) |
| Browser support | Chrome 90+, Edge 90+, Firefox 90+, Safari 15+ (requires color-mix() CSS support) |
| Export method | Client-side Blob and object URLs — no server required |
| Gap analysis | Runs entirely in browser memory |
| Stakeholder PDF | Browser print dialog — requires pop-ups to be allowed for the file origin |
| Dependencies | None (Google Fonts only, optional) |

---

## Microsoft Security Stack Coverage

| Product | Role in Dashboard |
|---|---|
| Microsoft Defender for Endpoint | Core EDR, AIR, Live Response, TVM, ASR, NGAV — primary subject of all tasks |
| Microsoft Defender XDR Portal | Alert management, incident correlation, Advanced Hunting, Threat Analytics, deception |
| Microsoft Intune | Endpoint Security policies, Security Baselines, device compliance, WUfB, disk encryption |
| Microsoft Entra ID | RBAC, Conditional Access, PIM, Credential Guard, CAE, device compliance signal |
| Microsoft Sentinel | SIEM/SOAR, analytics rules, UEBA, IR dashboards, audit log ingestion, workbooks |
| Defender Vulnerability Management | Exposure Score, CVE tracking, software inventory, EOS detection, remediation requests |
| Microsoft Defender for Identity | Lateral movement detection, honeytokens, identity behavioral analytics |
| Microsoft Defender for Cloud Apps | Shadow IT discovery, CASB policy, unsanctioned app blocking |
| Microsoft Purview | DLP endpoint enforcement, sensitivity label integration |
| Microsoft Security Copilot | AI-assisted investigation, incident summarisation (AI RMF governance tasks) |
| Power Automate and Logic Apps | Automated response flows, ITSM ticket creation, SOC notifications, Sentinel playbooks |
| Azure Key Vault | Service account credential storage and rotation for MDE API integrations |
| Windows Defender Application Control | Application allowlisting for PAW, CDE, and high-risk device groups |
| Windows Defender Firewall | Host-based network security control enforced via Intune Endpoint Security |

---

## Framework Reference Documents

| Framework | Version | Issuing Body | Primary Audience |
|---|---|---|---|
| NIST Cybersecurity Framework | 2.0 (February 2024) | NIST | All sectors — risk-based cybersecurity governance |
| Cyber Essentials | Current scheme | NCSC / IASME (UK) | UK organisations, supply chain compliance |
| Cyber Essentials Plus | Current scheme | NCSC / IASME (UK) | UK organisations requiring independent technical verification |
| SOC 2 | Trust Service Criteria 2017 (updated) | AICPA | SaaS, cloud, and managed service providers |
| NIST SP 800-53 | Revision 5 (September 2020) | NIST | Federal agencies, FedRAMP, high-assurance environments |
| PCI DSS | Version 4.0 (March 2022) | PCI Security Standards Council | Organisations processing, storing, or transmitting payment card data |
| NIST SP 800-207 | Zero Trust Architecture (August 2020) | NIST | Organisations implementing zero trust network architecture |
| NIST SP 800-37 | RMF Revision 2 (December 2018) | NIST | Federal agencies and organisations pursuing ATO |
| NIST AI 100-1 | AI RMF (January 2023) | NIST | Organisations developing, deploying, or procuring AI systems |

---

## Changelog

### v3.1
- Stakeholder Report scoped to per-framework use only — removed from Overview page and Actions dropdown
- Stakeholder Report export changed from HTML download to PDF via browser print dialog (window.print with A4 page layout and print-colour-adjust)
- Overview comparison section rebuilt from HTML table to responsive div layout — no horizontal scrolling on any screen size
- Category navigation replaced horizontal scrolling tab strip with a dropdown — defaults to All Controls on first load
- Framework switcher replaced horizontal scrolling pill row with a dropdown grouped into Dashboard and Frameworks sections
- Actions dropdown introduced — consolidates Import, Export, JSON Config, theme toggle, and GitHub feedback link into a single control
- All three dropdowns implement mutual close — opening one collapses the others
- Emojis removed from all dropdown items in the framework switcher and category dropdown

### v3.0
- Added PCI DSS v4.0 — 40 tasks across 8 requirement areas
- Added NIST Zero Trust SP 800-207 — 31 tasks across 6 ZT pillars
- Added NIST RMF SP 800-37 Rev 2 — 31 tasks across 7 RMF lifecycle steps
- Added NIST AI RMF AI 100-1 — 21 tasks across 4 AI RMF functions
- Total frameworks: 9 | Total tasks: approximately 270

### v2.1
- Added Cyber Essentials Plus — 35 tasks across 6 assessment categories
- Fixed "How to comply" toggle (duplicate ID bug resolved via DOM traversal)
- Added mobile-responsive layout (3 breakpoints)
- Added GitHub Issues feedback link in header and footer

### v2.0
- Added Gap Analysis feature — upload baseline JSON, compare delta, filter by type, export gap reports
- Added "How to comply" panels on all tasks — portal badge, navigation path, action, PowerShell/KQL blocks
- Added Import button with drag-and-drop file upload and validation

### v1.0
- Initial release with NIST CSF 2.0, Cyber Essentials, SOC 2, NIST 800-53
- Per-task status tracking, notes, dark/light mode, CSV/HTML/JSON export

---

MDE Multi-Framework Audit Tracker v3.1 | Built for MSSP Security Engineers | Microsoft Security Stack

Feedback and feature requests: https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues
