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

**Enterprise** - full control, IaaS (Infrastructure as a Service)

vs

**Cloud** - Splunk hosted, PaaS (Product as a Service), SaaS (Software as a Service)

### 🏗️ Splunk Architecture

A basic Splunk environment can be thought of as:

```text
💻 Data Sources - where the data is from
     ↓
📤 Universal Forwarders - in charge of ingestion to indexers, forward the data from the data searches
     ↓
📦 Indexers - The Indexer receives the data, stores and organises it, and makes it searchable. There are multiples present.
     ↓
🔎 Search Head
     ↓
👩‍💻 Analyst
```

### Data pipeline terminology

- Input - forwarders have the data, data=streams
- Parsing - processing of data, data=events
- License usage - license meter check
- Input types - files and directories
- Source - path of the data, method to collect the data
- Host - who sent the data
- Source type - data format

### App vs Add-on 
- You can create your own and publish them to Splunk
- Premium apps for extra costs - enterprise security, etc
- Apps - AWS, Azure, Corelight
- Add-on or TA (technology add-on) - something that runs in the background, no GUI - Juniper, Unix, and Linux
- There can be an add-on from the same vendor

### Knowledge Objects (KOs)

- Tools - conduct analysis, enrich your events
- A lot of things are KOS: fields, field extractions, a lookup, a tag, a field alias, a data model, and a saved search.
- Teamwork - every KO can be shared, reused, and searched based on permissions
- Knowledge Manager - oversees object creation, the person who provides centralised management for Splunk, eg, owner of a dashboard,
- Permissions can be: Private, This app only, or All apps (object persists globally across all apps)

### Fields
- Key value pairs
- Searchable by name
- Ability to search multiple fields at once
- Created by Splunk or recognised from an Add-on

### SPL - Search Processing Language
Syntax and colours:
- Orange - command modifiers: or, not, and, as, by
- Blue - the actual commands: stats, table, rename, dedup, sort, timechart
- Green - the arguments: limit, span
- Purple - the functions: tostring, sum, values, min, max, avg

### Transforming Command
- is a search command that orders the results into a data table, transforming searches
- Top - top number values of a field and puts them in a table
- rare does the opposite of top
- stats - calculate statistics - count, dc, sum, avg, list, values, etc 

### Transaction Command
- maxspan
- maxpause
- startwith & endswith
- events that span time
- grouping events
- aid investigations
- log validation

- transaction vs stats
- slow and will tax your environment vs faster, more efficient searching

### eval command 
- calculates fields, functions friendly, creates new fields, converting data
- where and search commands
- where, can't place before first | in the SPL, comparing values or searching where
- Search - place it anywhere in the SPL, search on a keyword, or match a value

### Fields in Splunk
- Fields are pieces of information Splunk extracts from raw events, such as username, status, IP address, or product.
- **Field extraction** means taking useful information out of raw event data and turning it into searchable fields.
  - There are two main approaches:
- rex → extracts fields using regular expressions (regex). Useful when the data is unstructured or doesn't have a consistent delimiter.
- erex → uses examples you provide to work out a pattern and extract the field, so you don't have to write the regex yourself.
#### Regex vs Delimiters
Regex is useful for unstructured data when you need to identify patterns.

**Example event:** Failed password for user john from 192.168.1.10

You could use rex to extract the IP:
```
| rex "from (?<ip>\d+\.\d+\.\d+\.\d+)"
```

Now Splunk creates an IP field containing 192.168.1.10.

- **Delimiters** are used when data has a consistent structure separating values, such as commas, spaces, or pipes.
Example: John,192.168.1.10,Failed

- The commas are the delimiters, making it easier to separate the data into fields.

**Commands**- rex and erex are SPL commands that you put into your search to extract fields.

## Visualise your data - Chart, timechart, stats

### `chart`

`chart` is used to create **visual comparisons between categories**.

Example:

```spl
index=main sourcetype=vendor_sales
| stats sum(price) by product_name
```

You could display this as a **bar chart** to compare sales between products.

**Think:** *Compare categories.*

---

### `timechart`

`timechart` is specifically for showing **changes over time**.

Example:

```spl
index=main sourcetype=access_*
| timechart count
```

This could create a **line graph showing website traffic over time**.

**Think:** *What's happening over time?*

---

### `stats`

`stats` is mainly used to **calculate and summarise data**. It doesn't automatically create a visual chart.

Example:

```spl
index=main sourcetype=vendor_sales
| stats sum(price) by product_name
```

It gives you a table showing the total price for each product. You can then choose a visualisation such as a bar chart.

**Think:** *Calculate and summarise.*

### `iplocation`

Adds **geographical information** to an IP address, such as country, city, latitude and longitude.

```spl
| iplocation src
```

**Think:** IP address → location information.

---

### `geostats`

Uses **latitude and longitude** to show where events are happening geographically, usually on a map.

```spl
| iplocation src
| geostats count by Country
```

- **latfield** → field containing latitude
- **longfield** → field containing longitude
- **globallimit** → maximum number of results shown globally
- **locallimit** → maximum number of results per location

**Think:** Turn location data into a geographical visualisation.

---

### `addtotals`

Adds values together to calculate **totals**.

```spl
| addtotals
```

For example, if a chart has several columns representing different categories, `addtotals` can add them together to create a total.

**Think:** Add everything together.

---

### `trendline`

Adds a **trend/moving average** to your results so you can see the general direction of the data rather than individual fluctuations.

Common types:

- **SMA** = Simple Moving Average
- **EMA** = Exponential Moving Average
- **WMA** = Weighted Moving Average

Example:

```spl
| trendline sma5 count
```

This calculates a **5-period simple moving average** of `count`.

## Reports and Drilldowns

### Reports
A **report** is a **saved search** in Splunk. Any search can be saved as a report and then **run whenever needed or scheduled** to run automatically. Reports should be **shareable** with other users.


### Drilldowns
A **drilldown** makes a dashboard **interactive**. When you click something in a panel, it can take you to a **search, another dashboard, or a report**.

**Think:** Click a result → investigate it further.

### `$tokens$`
**Tokens** allow you to pass the value you clicked from one panel to another search.

For example, clicking a hostname could pass:

```text
$click.value$
```

to another search, so Splunk shows information specifically about that host.

### Export
Splunk results can be **exported or printed**, including exporting a dashboard/report as a **PDF**.














- What are some of the options for deploying Splunk (Search Head)?
- What are some of the basic terms in Splunk?
- What type of data/files does Splunk usually ingest? CSV, JSON, log file, or txt file
- How can Splunk onboard/ingest data?
- What is SPL? Search Processing Language
- Show some basic examples of SPL:
- Basic searches
- Basic transformations
- Basic visualisations
- What are some of the things you can produce in Splunk (e.g. dashboards)?
- Best practices for securing data on Splunk? (optional)
- What are Splunk apps vs Splunk addons? Add-ons are packages used to bring in parse or normalise data, more of a backend thing. An app is a packaged set of dashboards, searches, configurations and KOs. It's bigger, and there are things that ppl already built.
- Case studies of Splunk being used?
- Security/SOC
- Data/business analysis
- Any others
- Best practices for securing data on Splunk?
- Splunk certification path? Certifications related to or helpful for SOC?
- Encrypting data in Splunk? (super optional)
- AI with Splunk? (super optional)
- Recommended datasets for Splunk? (super optional)
- Guides/walk-throughs/demos for Splunk? (Super optional)
- Make sure this README is professional-looking, has decent detail, is in your own words and features images/tables/bullet points where appropriate.
- Knowledge Object - reusable Splunk object. ex: saved search, field extractions, tags, macros, anything that you save
- Apps vs add-ons are packages used to bring in parse or normalise data
