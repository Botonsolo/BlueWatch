# BlueWatch: Modular SOC & Threat Detection Lab

> **Status:** In development

A personal cybersecurity lab focused on threat detection, endpoint monitoring, SOC alert investigation, and incident response.

## 🎯 Project Overview

BlueWatch aims to build a modular defensive security environment that reproduces the workflow of a Security Operations Center (SOC) analyst, from initial detection to evidence collection, investigation, and remediation recommendations.

The goal is not simply to generate alerts, but to investigate suspicious activity, validate findings using technical evidence, and justify every analytical conclusion.

## 🛡️ Planned Features

- **Endpoint Monitoring:** Collect Windows endpoint telemetry using Sysmon.
- **SIEM & Threat Detection:** Centralize and analyze security events using Wazuh.
- **SOC Alert Triage:** Investigate and classify alerts as True Positive (TP), False Positive (FP), or Inconclusive.
- **Threat Hunting:** Search for suspicious activity and correlate related events.
- **Malware Analysis:** Investigate malware behavior in a controlled, isolated environment.
- **IOC Management:** Document hashes, domains, IP addresses, file paths, and other indicators of compromise.
- **MITRE ATT&CK Mapping:** Map observed activity to documented adversary techniques when supported by evidence.
- **Incident Response:** Document containment, eradication, recovery, and remediation recommendations.
- **Technical Reporting:** Produce reproducible investigation reports supported by technical evidence.

> These features represent the project's objectives. Each feature will be marked as implemented only after it has been tested and validated.

## 🏗️ Proposed Architecture

```text
┌──────────────────────────────┐
│      Windows Endpoints       │
│           Sysmon             │
└──────────────┬───────────────┘
               │ Security Events
               ▼
┌──────────────────────────────┐
│            Wazuh             │
│     SIEM / Threat Detection  │
│     Rules / Alerts / Logs    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      SOC Investigation       │
│                              │
│  Alert Triage                │
│  Event Correlation           │
│  Process Analysis            │
│  Timeline Reconstruction     │
└────────┬─────────────┬───────┘
         │             │
         ▼             ▼
┌────────────────┐ ┌────────────────┐
│ Malware Sandbox│ │ Threat Intel   │
│ Isolated Lab   │ │ IOC Analysis   │
└────────┬───────┘ └────────┬───────┘
         └──────────┬───────┘
                    ▼
┌──────────────────────────────┐
│      Incident Reporting      │
│                              │
│  Evidence & Timeline         │
│  MITRE ATT&CK Mapping        │
│  Conclusions & Remediation   │
└──────────────────────────────┘
```

*This is a proposed logical architecture and will be updated as the project develops.*

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Wazuh | SIEM, event collection, and alerting |
| Sysmon | Detailed Windows endpoint telemetry |
| Windows / Linux | Laboratory endpoints and infrastructure |
| MITRE ATT&CK | Adversary tactics and techniques mapping |
| Python | Auxiliary scripts and automation |
| Bash | System administration and automation |
| Git | Version control and documentation |

Additional tools may be introduced as the project evolves.

## 🧪 Investigation Data Sources

Alert triage and investigation reports in this project are based on SOC simulators: TryHackMe's SOC rooms and Let's Defend. They provide realistic alerts, logs, and case workflows, so the time goes into analysis and reporting instead of building and attacking an environment first. The BlueWatch lab (Wazuh + Sysmon) is used for detection engineering and endpoint telemetry, and every report states whether its evidence comes from the lab or from a simulator.

All investigation reports and write-ups are published in [`security-writeups`](https://github.com/Botonsolo/security-writeups).

## 🔍 SOC Investigation Workflow

Each investigation will follow a structured and documented process:

1. **Detection:** Identify a security alert or suspicious event.
2. **Triage:** Assess the severity, context, and initial indicators.
3. **Evidence Collection:** Gather relevant logs, process information, and artifacts.
4. **Correlation:** Connect related events and reconstruct the activity timeline.
5. **Classification:** Determine whether the activity is malicious, legitimate, or inconclusive.
6. **IOC Extraction:** Document relevant indicators, including their source and context.
7. **MITRE ATT&CK Mapping:** Identify supported techniques when sufficient evidence is available.
8. **Response Recommendations:** Propose containment, remediation, and monitoring actions.
9. **Reporting:** Document findings, evidence, limitations, and conclusions.

## 📊 Investigation Reports

Each documented case should include:

- Case ID and executive summary.
- Date, time, and timezone.
- Environment and scope, including whether the evidence comes from the BlueWatch lab or a SOC simulator.
- Original alert and detection source.
- Relevant evidence and event references.
- Process relationships and command-line analysis.
- Timeline of observed activity.
- Technical reasoning and classification.
- Indicators of compromise (IOCs) and confidence level.
- MITRE ATT&CK techniques, when supported by evidence.
- Impact assessment and response recommendations.
- Limitations and reproduction steps.

All conclusions should be supported by evidence and documented so that another analyst can follow the investigation. Published reports are available in [`security-writeups`](https://github.com/Botonsolo/security-writeups).

## 🗺️ Development Roadmap

### Phase 1 — SOC Fundamentals
- [ ] Deploy Wazuh.
- [ ] Connect a Windows laboratory endpoint.
- [ ] Install and configure Sysmon.
- [ ] Validate event collection and visibility.
- [ ] Implement and test an initial detection rule.

### Phase 2 — Alert Investigation
- [ ] Develop practical detection use cases.
- [ ] Investigate process trees and command lines.
- [ ] Document true positives and false positives.
- [ ] Build investigation timelines.
- [ ] Tune detection rules to reduce false positives.

### Phase 3 — Threat Intelligence
- [ ] Define a consistent IOC format.
- [ ] Document indicator sources and confidence levels.
- [ ] Map observed activity to MITRE ATT&CK.
- [ ] Correlate indicators with laboratory evidence.

### Phase 4 — Malware Analysis
- [ ] Design an isolated and disposable analysis environment.
- [ ] Document network isolation and safety controls.
- [ ] Analyze behavior and collect relevant artifacts.
- [ ] Correlate sandbox findings with SIEM events.

### Phase 5 — Automation and Documentation
- [ ] Develop documented auxiliary scripts.
- [ ] Version and test detection rules.
- [ ] Publish reproducible investigation cases.
- [ ] Add verified dashboards and screenshots.
- [ ] Document implementation decisions and limitations.

## 📂 Repository Structure

- `detections/`: Wazuh rules with a description and test evidence
- `iocs/`: indicator tables
- `docs/`: architecture and setup notes

Investigation reports: [`security-writeups`](https://github.com/Botonsolo/security-writeups)

## 🔐 Security and Responsible Use

- Test only on systems you own or are explicitly authorized to assess.
- Analyze potentially malicious files only in an isolated, disposable environment.
- Never expose production systems or personal credentials to malware samples.
- Do not publish sensitive logs, credentials, tokens, or personal information.
- Sanitize screenshots and investigation artifacts before publication.
- Document the limitations of laboratory findings.

## ✅ Project Validation Criteria

BlueWatch will be considered demonstrable when it can show:

- [ ] Successful event collection from a laboratory endpoint.
- [ ] A detection rule producing the expected result in a controlled scenario.
- [ ] A traceable investigation supported by technical evidence (lab or simulator-based, stated in the report).
- [ ] A justified classification with documented reasoning.
- [ ] Response recommendations linked to the findings.
- [ ] Reproducible steps that another analyst can follow.

## 📌 Project Status

BlueWatch is a personal cybersecurity learning and portfolio project focused on **SOC Operations, Blue Team, Threat Detection, and Digital Forensics and Incident Response (DFIR)**.

The project prioritizes reproducibility, evidence-based analysis, technical documentation, and continuous improvement.

> **Transparency note:** Planned features must not be described as completed integrations until they have been implemented and validated.

## Disclaimer

Lab environment only. Samples are analysed in isolated, disposable machines. No real production data is included.
