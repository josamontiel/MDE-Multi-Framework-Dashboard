# MDE Multi-Framework Audit Tracker

A self-contained browser-based audit tracker for MSSP security engineers. Covers 10 compliance frameworks, approximately 347 Microsoft Defender for Endpoint-mapped tasks, per-task compliance guidance with portal navigation paths and PowerShell/KQL commands, product-based filtering, gap analysis, stakeholder PDF reporting, and full export support. No server, no login, no installation required.


---

<img width="796" height="655" alt="Screenshot 2026-03-27 at 20 56 31" src="https://github.com/user-attachments/assets/a85d4043-97cb-4c68-81b3-635a90368ba3" />

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

The MDE Multi-Framework Audit Tracker is a single HTML file designed for security engineers and analysts at Managed Security Service Providers working within the Microsoft Security ecosystem. It provides a structured, evidence-ready approach to deploying and auditing Microsoft Defender for Endpoint against ten compliance and risk management frameworks simultaneously.

Every task includes a "How to comply" panel containing the exact portal, navigation path, step-by-step action instructions, and for 71 tasks a ready-to-use PowerShell cmdlet or KQL query. Engineers know not just what needs doing, but precisely where and how to do it.

A product filter on each framework page lets engineers show only the tasks achievable through a specific Microsoft product — for example, filtering to Entra ID shows only the controls that require Entra configuration to achieve compliance.

The Gap Analysis feature compares a previously exported JSON configuration against the current state and classifies every task as compliant, improved, regressed, or still a gap.

The Stakeholder Report generates a plain-language executive summary scoped to the active framework, exportable directly to PDF via the browser's native print dialog.

All data lives in the browser. Nothing is transmitted externally. The entire tool is approximately 387 KB.

---

## Framework Coverage

### NIST CSF 2.0 — 55 Tasks
NIST Cybersecurity Framework 2.0 (February 2024)

| Function | ID | Tasks | MDE Focus |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory, tagging |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker, Conditional Access |
| Detect | DE | 10 | EDR sensor health, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, escalation matrix, playbooks |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis, quarterly health review |

---

### Cyber Essentials — 31 Tasks
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
| Logical & Physical Access | CC6 | 5 | MFA for portal, device compliance CA, RBAC access reviews, PIM |
| System Operations | CC7 | 5 | AIR automation, incident SLAs, Live Response audit, isolation test |
| Change Management | CC8 | 3 | Version-controlled baseline, policy approval workflow, audit log review |
| Risk Mitigation | CC9 | 3 | Third-party risk register, data residency/DPA, multi-tenant RBAC |

---

### NIST 800-53 Rev 5 — 36 Tasks
NIST SP 800-53 Revision 5 (September 2020)

| Family | ID | Tasks | MDE Focus |
|---|---|---|---|
| Access Control | AC | 5 | MDE RBAC, quarterly access reviews, Conditional Access, PIM |
| Audit & Accountability | AU | 5 | Admin audit logs, KQL queries, 12-month retention, event generation |
| Configuration Management | CM | 5 | Baseline version control, Security Baselines, ASR enforcement |
| Identification & Authentication | IA | 4 | Phishing-resistant MFA, PIM JIT, Key Vault credential storage |
| Incident Response | IR | 5 | IR plan, AIR workflows, Sentinel IR dashboard, escalation chain |
| Risk Assessment | RA | 3 | Secure Score/TVM baseline, continuous scanning, risk response decisions |
| System & Communications Protection | SC | 4 | Network Protection, WCF/DNS filtering, BitLocker, process isolation |
| System & Information Integrity | SI | 5 | NGAV, patch SLAs, EDR block mode, continuous monitoring, Tamper Protection |

---

### PCI DSS v4.0 — 40 Tasks
Payment Card Industry Data Security Standard v4.0

All tasks are scoped to cardholder data environment (CDE) device groups with evidence export instructions aligned to QSA assessment requirements.

| Category | Req | Tasks | MDE Focus |
|---|---|---|---|
| Network Security Controls | REQ1 | 6 | Host firewall for CDE, Network Protection, WCF, approved services register |
| Secure Configurations | REQ2 | 5 | CDE Security Baseline, service hardening, Tamper Protection, ASR |
| Malware Protection | REQ5 | 5 | NGAV for CDE, EDR block mode, 100% sensor coverage, anti-tampering |
| Vulnerability Management | REQ6 | 5 | TVM authenticated scan, 30-day patch SLA, EOS software, change control |
| Access Control & Authentication | REQ78 | 6 | MFA, CDE-scoped RBAC, PIM, quarterly access review, lockout policy |
| Audit Logging & Monitoring | REQ10 | 5 | Sentinel ingestion, 12-month retention, daily log review, immutability |
| Security Testing | REQ11 | 4 | Quarterly vuln scans, continuous IDS via EDR, Attack Simulator, FIM |
| Incident Response | REQ12 | 4 | PCI IR plan, AIR for CDE, card brand notification, annual IR test |

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
| Visibility & Analytics | ZT-VIS | 5 | MDE + Sentinel unified telemetry, ZT posture workbook, automated playbooks |

---

### NIST RMF SP 800-37 Rev 2 — 31 Tasks
NIST Risk Management Framework SP 800-37 Revision 2 (December 2018)

| Step | ID | Tasks | RMF Focus |
|---|---|---|---|
| Prepare | PR | 5 | Risk strategy, AO/ISSO/ISSM roles, system boundary, inherited controls |
| Categorize | CAT | 4 | FIPS 199 impact levels, information types, data flow diagram |
| Select | SEL | 4 | 800-53 baseline selection, control tailoring, SSP control table |
| Implement | IMP | 5 | Technical control deployment, SSP narratives, operational policies |
| Assess | ASS | 4 | Security Assessment Plan, MDE control testing, SAR, POA&M |
| Authorize | AUT | 4 | Authorisation package, risk determination, ATO memo |
| Monitor | MON | 5 | Ongoing monitoring, Secure Score/TVM metrics, AO status reports |

---

### NIST AI RMF AI 100-1 — 21 Tasks
NIST Artificial Intelligence Risk Management Framework (January 2023)

Addresses AI and ML-powered capabilities within MDE: Automated Investigation and Remediation, ML-based alert prioritisation, anomaly detection, behavioral threat scoring, and Microsoft Security Copilot.

| Function | ID | Tasks | AI Risk Focus |
|---|---|---|---|
| Govern | AI-GV | 6 | AI governance policy, accountability roles, AI use policy, human oversight |
| Map | AI-MAP | 5 | AI feature inventory, automated action impact mapping, FP risk assessment |
| Measure | AI-MEA | 5 | FP/FN rate tracking, AIR accuracy measurement, model drift monitoring |
| Manage | AI-MAN | 5 | Human-in-the-loop enforcement, AI override escalation, detection tuning |

---

### GDPR — 36 Tasks
EU General Data Protection Regulation 2016/679

Maps Microsoft Defender for Endpoint and the Microsoft Security stack to GDPR obligations covering security of processing, breach detection and notification, privacy by design, access control and accountability, and DPO governance requirements.

| Article | ID | Tasks | MDE Focus |
|---|---|---|---|
| Art 32 Security of Processing | ART32 | 8 | BitLocker, NGAV, EDR coverage, Tamper Protection, patch SLA, Art 32 documentation |
| Art 33/34 Breach Notification | ART3334 | 6 | Breach detection workflow, MDE alert routing, Sentinel breach analytics, 72-hr procedure |
| Art 25 Privacy by Design | ART25 | 6 | Device control for data minimisation, CFA for data integrity, Purview DLP, WDAC |
| Art 5/32 Access Control | ACCTRL | 7 | MFA enforcement, MDE RBAC, PIM for privileged access, access reviews, inactive accounts |
| Art 32 Audit & Accountability | AUDIT | 5 | Defender audit logs, Sentinel ingestion, 12-month retention, immutability, daily review |
| Art 37/39 DPO & Governance | DPO | 4 | DPO notification routing, ROPA documentation, processor agreements, privacy training |

---

## Feature Reference

### How to Comply — Per-Task Compliance Guidance

Every task has a collapsible "How to comply" panel. Each panel contains three components.

**Portal badge and navigation path** — a colour-coded badge identifying which Microsoft portal or tool is required, alongside the exact menu trail to the relevant setting.

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

**Command and Query block** (71 tasks) — a ready-to-use PowerShell cmdlet or KQL query for verification or automation.

---

### Product Filter

Each framework page includes a product filter bar directly below the category dropdown. It shows one button per Microsoft product that has at least one task in the active framework. Each button displays the product name and a count of how many tasks in the framework require that product.

Clicking a product button instantly hides all tasks whose "How to comply" guidance references a different product. This lets engineers focus on exactly the controls relevant to a specific product they are configuring — for example, filtering to Entra ID shows only the controls where Entra configuration is the path to compliance.

The filter works across all categories. Switching between category views while a filter is active keeps the filter applied. If a category has no tasks for the selected product, a clear message is shown rather than an empty section. The navigation info line updates to show how many controls are visible out of the total.

Clicking an active filter button, or clicking the "Clear filter" link that appears when a filter is active, restores all tasks. The filter resets when navigating to a different framework.

---

### Gap Analysis

The Gap Analysis tab compares a previously exported JSON configuration against the current tracker state across all frameworks simultaneously.

Upload a baseline via the Import option in the Actions dropdown. Files are validated client-side before processing.

Once loaded, every task is classified with a delta type:

| Delta | Meaning |
|---|---|
| Compliant | Complete in both baseline and current state |
| Improved | Not complete in baseline, now complete |
| Regression | Was complete in baseline, no longer complete — requires investigation |
| Gap | Not complete in either — unresolved control |
| Blocked | Currently blocked in the active tracker |
| In Progress | Work started but not finished |
| New Control | Task not present in the uploaded baseline |

An overall compliance score is calculated as the percentage of controls that are Compliant or Improved. Filters allow drilling into a single delta type across all frameworks. Gap-specific CSV and HTML exports are available from within the Gap Analysis view.

---

### Stakeholder Report

Each framework view includes a Stakeholder Report button in the framework header. It generates a plain-language executive summary scoped to the active framework, built in real time from current tracker state.

The report contains four sections: Executive Summary (narrative posture description), Framework Status (completion bars and plain status labels), Risk Indicators (auto-generated from blocked controls, incomplete high-priority tasks, and low-coverage frameworks), and Recommended Next Steps (the specific next high-priority task for each lowest-progress area).

Clicking Export as PDF opens a print-optimised version in a new browser tab and triggers the native print dialog. Select "Save as PDF" as the destination. The report uses A4 layout with section breaks and forced colour rendering. If the browser blocks the pop-up, allow pop-ups from the file origin and try again.

The Stakeholder Report is available only within individual framework views, not on the Overview page.

---

### Dashboard Overview

The Overview page shows all ten frameworks as summary cards with live completion percentages and a comparison section listing every framework as a responsive row with a progress bar, status breakdown, and an Open button. The comparison section reflows at all screen sizes with no horizontal scrolling.

---

### Navigation

**Framework switcher** — in the header, opens a dropdown grouped into Dashboard (Overview, Gap Analysis) and Frameworks (all ten). Each framework item shows a live done/total count. A LIVE badge appears on Gap Analysis when a baseline is loaded.

**Actions dropdown** — in the header, groups all utility actions: Data (Import Config, Export, JSON Config), Appearance (Dark/Light theme toggle pill), and Links (Report Issue on GitHub).

**Category dropdown** — within each framework view, lists all categories with descriptions, done/total counts, and mini progress bars. Defaults to All Controls on first load.

Opening any dropdown automatically closes the others.

---

### Per-Task Tracking

Each task supports four states: Not Started, In Progress, Complete, Blocked. Update via dropdown or checkbox. Completed tasks receive a visual strikethrough. A notes field holds ticket references, evidence links, or blocker descriptions. All state saves automatically to localStorage on every interaction.

---

### Mobile Friendly

Three responsive breakpoints: tablet (900px), mobile (768px), and small mobile (480px). All dropdowns are inherently compact. Task rows restack to single-column on mobile. The comparison section and category navigation have no horizontal scrolling at any size.

---

### Dark and Light Mode

Toggle in the Actions dropdown using a pill control. Persists across sessions.

---

### Export Options

| Format | Content | Typical Use |
|---|---|---|
| CSV | All frameworks — task ID, name, reference, priority, status, notes | Excel or Sheets for custom reporting |
| HTML Report | All frameworks — full audit report with coloured section headers | Client delivery, auditor submission |
| JSON Config | Active framework or all — structured config with metadata | Version control, gap analysis baseline, GRC ingestion |
| Gap CSV | All frameworks — baseline status, current status, delta classification | Client-facing gap report |
| Gap HTML Report | All frameworks — compliance score, delta breakdown, per-task comparison | Pre-assessment remediation plan |
| Stakeholder PDF | Active framework — executive summary, risks, next steps | Client QBRs, CISO briefings, board reporting |

---

### Feedback and Issue Reporting

A Feedback link in the Actions dropdown and a footer link both point to the GitHub Issues page.

Repository: https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues

---

## Use Cases

### 1. New Client MDE Onboarding (MSSP)
Export a JSON config at project start as the deployment baseline. Work through tasks using the "How to comply" guidance. Use the product filter to focus sessions on a single product — complete all Intune tasks in one session, all Entra tasks in another. Export the HTML report at project close. Generate the Stakeholder Report PDF for the client's security leadership.

### 2. GDPR Article 32 Compliance Documentation
Use the GDPR framework to map MDE configurations to specific GDPR articles. The Art 32 tasks cover encryption, malware protection, EDR coverage, patch management, and the formal Article 32 technical measures document that supervisory authorities and processors expect. Filter to Intune or Defender Portal to focus on a specific product area.

### 3. Pre-Assessment Gap Analysis
Upload the client's existing JSON baseline before a formal audit. The gap analysis surfaces regressions, unresolved gaps, and controls never addressed. Export the gap report as the pre-assessment remediation plan.

### 4. PCI DSS QSA Assessment Support
Use the PCI DSS framework with tasks scoped to CDE device groups. Evidence export instructions in "How to comply" panels are written for QSA requirements. Generate the Stakeholder Report PDF for the client's finance and compliance team.

### 5. Cyber Essentials and CE Plus Certification
Use CE for base control readiness and CE+ for assessment preparation. Every CE+ task describes what to test live and what the assessor will verify.

### 6. SOC 2 Type II Continuous Monitoring
Track CC controls with ticket numbers and approval evidence in notes. Export JSON monthly as point-in-time monitoring evidence. Import the previous month's export to confirm no regressions before the auditor review period.

### 7. NIST 800-53 and FedRAMP SSP Development
Use the 800-53 framework alongside KQL/PowerShell commands to document MDE control implementations in SSP narratives. Export JSON for GRC platform ingestion.

### 8. NIST RMF ATO Lifecycle Management
Work through the seven RMF steps in sequence. Each task maps to a specific RMF deliverable — categorisation document, SSP control table, SAP, SAR, POA&M, ATO memo.

### 9. Zero Trust Architecture Programme Tracking
Track progress across all six ZT pillars simultaneously. Filter by Entra ID to see all identity-layer controls, or by Intune to see all device-layer controls in one focused view.

### 10. AI Risk Management for Automated SOC Tools
Use the AI RMF framework to govern MDE's automated capabilities before expanding AIR automation levels. Tasks cover governance policy, impact mapping, FP rate measurement, and AI incident handling.

### 11. GDPR Breach Notification Readiness
Use the GDPR Breach Notification category to verify detection and notification workflows are in place before a supervisory authority assessment. "How to comply" guidance covers Sentinel analytics rules for exfiltration patterns and the formal 72-hour notification procedure document.

### 12. Product-Focused Engineering Sessions
Use the product filter to organise work by Microsoft product rather than by compliance framework. An engineer tasked with all Entra configuration across the engagement can open each framework, filter to Entra ID, and work through only those tasks — eliminating context-switching across unrelated portals.

### 13. Client QBR Preparation
Open the target framework, click Stakeholder Report, and export as PDF. The plain-language summary with completion percentage, risk indicators, and recommended next steps gives the client's leadership team a complete picture without requiring technical context.

### 14. GitOps Compliance Versioning
Export JSON after each sprint and commit to a git repository. Import any previous export for gap analysis to see exactly what changed between periods. This creates a full version history suitable for SOC 2 continuous monitoring evidence.

### 15. Multi-Framework Simultaneous Audit
For clients with overlapping obligations — GDPR, PCI DSS, Cyber Essentials, and SOC 2 simultaneously — track all frameworks in parallel. The Overview comparison section shows all compliance obligations at a glance.

---

## Getting Started

1. Download `mde-multi-audit-dashboard.html`
2. Open in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, build tools, login, or internet connection required after initial load
4. Use the Overview page for a cross-framework status summary
5. Select a framework from the header framework switcher
6. Use the product filter bar to focus on controls for a specific Microsoft product
7. Click any task's "How to comply" button to expand compliance guidance
8. Update task statuses and notes — all changes save automatically
9. Use the Actions dropdown to Import a baseline JSON for gap analysis, Export data, or toggle the theme
10. Open any framework and click Stakeholder Report to generate a PDF-ready executive summary

---

## Data and Privacy

All task state, notes, and preferences are stored exclusively in browser localStorage under the key `mde-multi-state-v2`. Nothing is transmitted to any external server. The dashboard is fully offline-capable after the initial Google Fonts load.

Uploaded baseline files for gap analysis are processed entirely in browser memory and never transmitted externally. The Stakeholder Report PDF is generated client-side via a new browser window and the native print dialog — no data leaves the device.

To transfer state to another machine, export the JSON config and import it on the destination, or copy the localStorage value directly via browser developer tools under Application > Local Storage.

---

## Technical Notes

| Property | Detail |
|---|---|
| Format | Single self-contained .html file |
| File size | Approximately 387 KB uncompressed |
| Frameworks | 10 |
| Total tasks | Approximately 347 |
| Tasks with PowerShell or KQL | 71 |
| Fonts | Syne (headings), JetBrains Mono (code/metrics), DM Sans (UI) via Google Fonts |
| State storage | localStorage — key mde-multi-state-v2 (tasks), mde-theme (theme) |
| Browser support | Chrome 90+, Edge 90+, Firefox 90+, Safari 15+ (requires color-mix() CSS support) |
| Export method | Client-side Blob and object URLs — no server required |
| Gap analysis | Runs entirely in browser memory |
| Stakeholder PDF | Browser print dialog — requires pop-ups to be allowed for the file origin |
| Product filter | CSS class toggling on data-portal attributes — no re-render, instantaneous |
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
| Microsoft Purview | DLP endpoint enforcement, sensitivity label integration, data classification |
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
| PCI DSS | Version 4.0 (March 2022) | PCI Security Standards Council | Organisations processing payment card data |
| NIST SP 800-207 | Zero Trust Architecture (August 2020) | NIST | Organisations implementing zero trust architecture |
| NIST SP 800-37 | RMF Revision 2 (December 2018) | NIST | Federal agencies and organisations pursuing ATO |
| NIST AI 100-1 | AI RMF (January 2023) | NIST | Organisations developing, deploying, or procuring AI systems |
| EU GDPR | Regulation 2016/679 | European Parliament / Council | All organisations processing personal data of EU residents |

---

## Changelog

### v3.2
- Added GDPR framework — 36 tasks across six categories: Security of Processing (Art 32), Breach Notification (Art 33/34), Privacy by Design (Art 25), Access Control and Accountability, Audit and Logging, and DPO Governance (Art 37/39)
- Added product filter bar to every framework view — filters tasks by Microsoft product based on "How to comply" portal assignments; supported products are Defender Portal, Microsoft Intune, Entra ID, Sentinel, PowerShell, M365 Admin, Azure Portal, and Internal Process
- Fixed TypeError on framework switcher dropdown caused by GDPR being defined in the FW data object but missing from the fwMeta lookup table in renderSwitcher

### v3.1
- Navigation overhaul — framework switcher, category selector, and action buttons all converted to dropdown controls
- Overview page comparison section rebuilt as a fully responsive layout replacing the HTML table
- Stakeholder Report scoped to individual framework views only, removed from Overview page and Actions dropdown
- Stakeholder Report export changed from HTML download to PDF via browser print dialog
- All emojis removed from dropdown navigation controls
- Opening any dropdown automatically closes the others

### v3.0
- Added PCI DSS v4.0 (40 tasks), NIST Zero Trust SP 800-207 (31 tasks), NIST RMF SP 800-37 Rev 2 (31 tasks), NIST AI RMF AI 100-1 (21 tasks)
- Total after this release: 9 frameworks, approximately 270 tasks

### v2.1
- Added Cyber Essentials Plus (35 tasks)
- Fixed "How to comply" toggle duplicate ID bug via DOM traversal
- Added mobile-responsive layout (3 breakpoints)
- Added GitHub Issues feedback link

### v2.0
- Added Gap Analysis feature with baseline import, delta classification, compliance score, filters, and gap exports
- Added "How to comply" panels to all tasks with portal badge, navigation path, action instructions, and PowerShell/KQL blocks
- Added Import button with drag-and-drop file upload

### v1.0
- Initial release with NIST CSF 2.0, Cyber Essentials, SOC 2, NIST 800-53
- Per-task status tracking, notes, dark/light mode, CSV/HTML/JSON export

---

MDE Multi-Framework Audit Tracker v3.2 | Built for MSSP Security Engineers | Microsoft Security Stack

Feedback and feature requests: https://github.com/josamontiel/MDE-Multi-Framework-Dashboard/issues
