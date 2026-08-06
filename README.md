# Splunk Upskilling

## What is SOC?
SOC - Security Operations Centre
SOC is a team that monitors an organisation's systems for cyber threats. They detect, investigate and respond to suspicious activity.

### Key Functions
- Monitoring – Watch systems, networks and logs for suspicious activity.
- Detection – Identify potential cyber threats and security incidents.
- Incident response – Work out whether an alert is a real threat or a false alarm.
- Threat intelligence – understand current and emerging threats.
- Security analysis – analyse data to understand risks and attacks.
- Security reporting – provide information about security activity and incidents.

### Common Technologies
- EDR – Monitors computers/devices for suspicious activity.
- Firewall – Controls network traffic and blocks unwanted connections.
- IDS/IPS – Detects and/or blocks suspicious network activity.
- SOAR – Automates security tasks and responses.
- Threat Intelligence – Provides information about known threats, attackers and malicious IPs/files.
- Vulnerability scanners – Find weaknesses in systems and applications.

### Processes
The SOC process involves identifying a suspicious event, understanding it, dealing with it, and ensuring it doesn't happen again.

Detect → Triage → Investigate → Contain → Eradicate → Recover → Review

### Best Practices
1. Align strategy with business goals
2. Adopt the people, process, and technology (PPT) model
3. Build a proactive threat detection strategy
4. Roll out incident response (IR) plans and playbooks for a range of scenarios
5. Opt for a risk-based approach
6. Automation and orchestration

### Roles

**Tier 1 SOC Analyst** - This role involves basic troubleshooting and is usually the first point of contact for clients or customers. It can also mean monitoring and analysing security alerts.

**Tier 2 SOC Analyst** - This tier handles escalated issues involving more complex software or network problems. They look at logs, user activity, IP addresses and other evidence to understand what happened and how serious the incident is.

**Tier 3 SOC Analyst** - Deals with more complex security incidents. They may perform deeper investigations that require more time and engineering effort, and help improve the organisation's security detection.

There are also other roles, such as Incident Responder, Threat Hunter, Security Engineer, and SOC Manager.

A **Threat Hunter** proactively searches the organisation's data and systems for signs of attackers that may not yet have triggered an alert. Instead of waiting for something to happen, they actively search for threats.

```text
Triage - Reactive, starts from alerts. Focuses on validation.

vs 

Threat Hunting - Proactive, starts from a hypothesis. Focuses on discovery.
```

### Challenges 

A SOC can face too many alerts (too much data), false positives, alert fatigue, a lack of skilled staff, difficulty responding quickly to real threats, insider threats and keeping up to date with new threats.

### Common Event Types in a SOC

- An event is anything that happens in a network/computer/software. A SOC monitors events that could indicate **normal activity, suspicious behaviour or an attack**. An event has a timestamp, raw eventtext, and a host (where the event is happening), a source (who), and extracted fields.

| Event | Example |
|---|---|
| 🔑 Login | Successful or failed login |
| 🌐 Network | Unusual connection or IP address |
| 📁 File | File created, deleted or accessed |
| 🛡️ Firewall | Connection blocked |
| 🦠 Malware | Malware detected |
| 👤 Account | New user or permission change |
| 💻 System | System/service started or stopped |

## What is SIEM?

SIEM (**Security Information and Event Management**) - a SIEM collects security events from different systems, aggregates them, and analyses them to help security teams detect and investigate threats.

I think of SIEM like a smart home security system. It has a camera that detects unusual movement, a door sensor, an app to alert the owner, and a report of detected activity. In cybersecurity, a SIEM works similarly:

```text
💻 Systems ──┐
🌐 Network ──┤
🛡️ Firewall ─┼──→ 🧠 SIEM ──→ 👩‍💻 SOC Analyst
☁️ Cloud ────┤
📧 Email ────┘

```

- Some examples of SIEM are **Splunk**, IBM Security and Microsoft Sentinel. Open source is popular because it is free.

### What is Splunk and why use it?

- Splunk is a SIEM platform used because it brings large amounts of data into one searchable place, making it easier to spot problems and investigate them quickly.

**Versions of Splunk**

Enterprise - full control, IaaS (Infrastructure as a Service)

vs

Cloud - Splunk hosted, PaaS (Product as a Service), SaaS (Software as a Service)

### 🏗️ Splunk Architecture

A basic Splunk environment can be thought of as:

```text
💻 Data Sources
     ↓
📤 Universal Forwarders - in charge of ingestion to indexers, forward the data from the data searches
     ↓
📦 Indexers - The Indexer receives the data, stores and organises it, and makes it searchable. There are multiples present.
     ↓
🔎 Search Head
     ↓
👩‍💻 Analyst
```

