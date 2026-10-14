
# BlueWatch — Modular SOC & Threat Detection Lab

> **Estado:** Proyecto en desarrollo.  
> Laboratorio personal de ciberseguridad defensiva orientado a la monitorización, detección de amenazas, investigación de alertas y respuesta a incidentes.

## 🎯 Objetivo

BlueWatch busca construir un entorno modular que permita reproducir el flujo de trabajo de un analista SOC, desde la detección inicial hasta la documentación de las evidencias y las recomendaciones de respuesta.

El objetivo no es únicamente generar alertas, sino investigar qué ha ocurrido, validar las evidencias y justificar cada conclusión técnica.

## 🛡️ Funcionalidades previstas

- **Endpoint Monitoring:** recopilación de eventos de sistemas Windows mediante Sysmon.
- **SIEM & Threat Detection:** centralización y análisis de eventos con Wazuh.
- **SOC Alert Triage:** investigación y clasificación de alertas como True Positive (TP), False Positive (FP) o inconclusas.
- **Threat Hunting:** búsqueda de actividad sospechosa y correlación de eventos.
- **Malware Analysis:** análisis controlado del comportamiento de muestras en un entorno aislado.
- **IOC Management:** documentación de hashes, dominios, direcciones IP y otros indicadores.
- **MITRE ATT&CK:** identificación de técnicas respaldadas por evidencias.
- **Incident Response:** documentación de contención, erradicación, recuperación y medidas correctivas.
- **Technical Reporting:** elaboración de informes reproducibles con evidencias y conclusiones.

> Estas funcionalidades representan los objetivos del proyecto. Cada una se marcará como implementada cuando exista una prueba verificable.

## 🏗️ Arquitectura propuesta

```text
┌──────────────────────────────┐
│      Windows Endpoints       │
│          Sysmon              │
└──────────────┬───────────────┘
               │ Events
               ▼
┌──────────────────────────────┐
│            Wazuh             │
│     SIEM / Threat Detection  │
│     Rules / Alerts / Logs    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        SOC Investigation      │
│                              │
│  Alert Triage                 │
│  Event Correlation            │
│  Process Analysis             │
│  Timeline Reconstruction      │
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
│       Incident Reporting     │
│                              │
│  Evidence & Timeline         │
│  MITRE ATT&CK Mapping        │
│  Conclusions & Remediation   │
└──────────────────────────────┘
```

*La arquitectura es una propuesta y se actualizará según avance la implementación.*

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Wazuh | SIEM, event collection and alerting |
| Sysmon | Windows endpoint telemetry |
| Windows / Linux | Laboratory endpoints and infrastructure |
| MITRE ATT&CK | Adversary tactics and techniques mapping |
| Python | Auxiliary scripts and automation |
| Bash | System administration and automation |
| Git | Version control and documentation |

Additional tools may be incorporated as the project evolves.

## 🔍 SOC Investigation Workflow

Each investigation will follow a documented process:

1. **Detection:** identify an alert or suspicious event.
2. **Triage:** assess severity, context and initial indicators.
3. **Evidence Collection:** gather relevant logs, process information and artifacts.
4. **Correlation:** connect related events and reconstruct the activity timeline.
5. **Classification:** determine whether the activity is malicious, legitimate or inconclusive.
6. **IOC Extraction:** document relevant indicators with their source and context.
7. **MITRE ATT&CK Mapping:** identify supported techniques when evidence allows.
8. **Response Recommendations:** propose containment, remediation and monitoring actions.
9. **Reporting:** record findings, evidence, limitations and conclusions.

## 📂 Repository Structure

```text
BlueWatch/
├── README.md
├── docs/
│   ├── architecture.md
│   ├── roadmap.md
│   └── lab-safety.md
├── detections/
│   ├── wazuh/
│   └── sysmon/
├── cases/
│   └── CASE-0001-example/
│       ├── README.md
│       ├── evidence/
│       ├── timeline.csv
│       ├── iocs.csv
│       └── report.md
├── scripts/
├── dashboards/
└── .gitignore
```

This is the proposed repository structure and may change as components are implemented.

## 📊 Investigation Reports

Each documented case should include:

- Case ID and summary.
- Date, time and timezone.
- Environment and scope.
- Original alert and detection source.
- Relevant evidence and event references.
- Process relationships and command-line analysis.
- Timeline of activity.
- Technical reasoning and classification.
- IOCs and confidence.
- MITRE ATT&CK techniques, where supported.
- Impact assessment and response recommendations.
- Limitations and reproduction steps.

Evidence should support the conclusions and allow another analyst to follow the investigation.

## 🗺️ Roadmap

### Phase 1 — SOC Fundamentals
- [ ] Deploy Wazuh.
- [ ] Connect a Windows laboratory endpoint.
- [ ] Install and configure Sysmon.
- [ ] Validate event collection.
- [ ] Implement and test an initial detection rule.

### Phase 2 — Alert Investigation
- [ ] Develop practical detection use cases.
- [ ] Investigate process trees and command lines.
- [ ] Document true positives and false positives.
- [ ] Build investigation timelines.
- [ ] Tune detection rules to reduce false positives.

### Phase 3 — Threat Intelligence
- [ ] Define a consistent IOC format.
- [ ] Document indicator sources and confidence.
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

## 🔐 Security and Responsible Use

- Test only on systems you own or are explicitly authorized to assess.
- Analyze potentially malicious files only in an isolated, disposable environment.
- Never expose production systems or personal credentials to malware samples.
- Do not publish sensitive logs, credentials, tokens or personal information.
- Sanitize screenshots and investigation artifacts before publication.
- Document the limitations of laboratory findings.

## ✅ Project Validation Criteria

BlueWatch will be considered demonstrable when it can show:

- [ ] Successful event collection from a laboratory endpoint.
- [ ] A detection rule producing the expected result in a controlled scenario.
- [ ] A traceable investigation supported by technical evidence.
- [ ] A justified classification and documented reasoning.
- [ ] Response recommendations linked to the findings.
- [ ] Reproducible steps that another analyst can follow.

## 📌 Project Status

BlueWatch is a personal learning and portfolio project focused on **SOC operations, Blue Team, threat detection and DFIR**.

The project prioritizes reproducibility, evidence-based analysis, technical documentation and continuous improvement.

> **Transparency note:** planned features must not be described as completed integrations until they have been implemented and validated.
