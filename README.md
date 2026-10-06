&#x20;SOC Threat Hunting & Multi-Source Log Correlation Using Splunk SIEM



&#x20;Overview



This project simulates a Tier-1 SOC analyst investigation using Splunk as the SIEM platform. The lab focuses on analyzing and correlating multiple security telemetry sources to identify suspicious activity and reconstruct an investigation timeline.



The environment uses Apache web logs, simulated firewall logs, and Windows Security logs generated and analyzed in a controlled virtual lab.


&#x20;Architecture


&#x20;                   ┌─────────────────────┐

&#x20;                   │     Splunk SIEM     │

&#x20;                   │ Search / Correlation│

&#x20;                   │    Dashboards       │

&#x20;                   └──────────┬──────────┘

&#x20;                              │

&#x20;            ┌─────────────────┼─────────────────┐

&#x20;            │                 │                 │

&#x20;            ▼                 ▼                 ▼

&#x20;     ┌────────────┐    ┌────────────┐    ┌──────────────┐

&#x20;     │   Apache   │    │  Firewall  │    │   Windows    │

&#x20;     │ Access Log │    │    Logs    │    │ Security Log │

&#x20;     └────────────┘    └────────────┘    └──────────────┘

&#x20;            │                 │                 │

&#x20;            └─────────────────┼─────────────────┘

&#x20;                              ▼

&#x20;                    Threat Hunting \& 

&#x20;                  Cross-Source Analysis

&#x20;                              │

&#x20;                              ▼

&#x20;                    Investigation Timeline



Data Sources



Apache Access Logs



Used to investigate:

\- Requests to /admin

\- Requests to /login

\- Requests to /phpmyadmin

\- HTTP 404 responses

\- Suspicious web request patterns

\- SQL-like request patterns such as union select



Firewall Logs



Used to examine:

\- Repeated connection attempts

\- Source addresses

\- Target ports

\- Allowed and blocked traffic

\- Frequency and timing of network activity



Windows Security Logs



Authentication activity was analyzed using:

\- Event ID 4625 — failed logon

\- Event ID 4624 — successful logon



Threat Hunting



The investigation followed a hypothesis-driven workflow:

Telemetry

&#x20;   ↓

Initial hypothesis

&#x20;   ↓

Search and filtering

&#x20;   ↓

Identify suspicious activity

&#x20;   ↓

Cross-source correlation

&#x20;   ↓

Timeline reconstruction

&#x20;   ↓

Analyst assessment

&#x20;   ↓

Recommended controls



Investigation Findings



The controlled investigation identified:

\- Repeated requests targeting sensitive web paths.

\- High-frequency HTTP 404 responses associated with resource probing.

\- Multiple failed authentication attempts.

\- Successful authentication events following failed attempts.

\- Repeated network connection activity in firewall telemetry.

\- Suspicious web request patterns including union select.



These observations were assessed as indicators requiring further investigation rather than being treated as definitive proof of successful compromise.



Splunk Analysis



The project demonstrates:

\- SPL-based searching and filtering

\- Log source analysis

\- Cross-source correlation

\- Time-based investigation

\- Authentication monitoring

\- Web traffic analysis

\- Dashboard-based SOC monitoring



Dashboards



The project includes dashboard use cases for:

1\. Authentication success versus failure

2\. Web traffic and suspicious request activity



Investigation Approach



Each source was initially analyzed independently. Relevant source addresses, timestamps, request patterns, authentication events, and network activity were then compared to identify temporal relationships and reconstruct the likely sequence of activity.



Temporal correlation was treated as supporting evidence and not, by itself, as proof that events originated from the same attack.



Limitations



This is a controlled cybersecurity lab using simulated and locally generated telemetry.

The available evidence demonstrates suspicious activity patterns and cross-source investigation techniques. It does not establish that a real external attacker successfully compromised a production system.



Technologies



\- Splunk

\- SPL

\- Apache

\- Windows Security Logs

\- Firewall Logs

\- Kali Linux

\- VirtualBox

\- Linux command-line utilities



 Project Outcome

This project provided hands-on practice with SIEM-based threat hunting, multi-source log analysis, SPL searching, event correlation, timeline reconstruction, and SOC dashboarding in a controlled environment.

Key capabilities demonstrated:

- Ingesting and analyzing multiple security log sources in Splunk
- Investigating suspicious web requests and potential reconnaissance activity
- Analyzing Windows authentication activity
- Examining firewall connection activity
- Correlating activity across different log sources
- Performing time-based threat hunting
- Building SOC monitoring dashboards
- Documenting an analyst-oriented investigation workflow



