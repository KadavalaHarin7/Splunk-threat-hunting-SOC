&#x20;Investigation Timeline



&#x20;Purpose



This timeline organizes the observed activity from the Apache, firewall, and Windows Security telemetry into a chronological investigation sequence.



&#x20;Observed Activity



&#x20;1. Network Activity



Firewall telemetry showed repeated connection attempts, including activity involving commonly targeted ports.



The investigation considered:



\- Source IP address

\- Destination port

\- Connection frequency

\- Allowed versus blocked traffic

\- Event timing



&#x20;2. Web Reconnaissance



Apache logs showed repeated requests targeting sensitive paths, including:



\- `/admin`

\- `/login`

\- `/phpmyadmin`



A high frequency of HTTP 404 responses was also observed, consistent with probing for resources that were not available.



&#x20;3. Suspicious Web Requests



Splunk searches were used to identify suspicious request patterns, including:



\- `union`

\- `../`

\- `/admin`

\- `/phpmyadmin`



The `union select` pattern was treated as a SQL-injection-style indicator requiring investigation.



&#x20;4. Authentication Activity



Windows Security telemetry showed:



\- Event ID 4625 — failed logon attempts

\- Event ID 4624 — successful logon



Repeated failed attempts followed by successful authentication were treated as an investigation lead.



&#x20;5. Cross-Source Correlation



Source addresses and timestamps from the different log sources were compared to determine whether the observed activity formed a consistent sequence.



The investigation therefore followed the general progression:



Connection Activity

&#x20;       ↓

Web Reconnaissance

&#x20;       ↓

Suspicious Web Requests

&#x20;       ↓

Authentication Failures

&#x20;       ↓

Successful Authentication

&#x20;       ↓

Cross-Source Investigation



Analyst Assessment



The observed telemetry is consistent with suspicious reconnaissance and authentication activity in the controlled lab environment.



The evidence supports investigation of potentially malicious behavior, but it does not independently establish successful compromise of a production system.



Evidence Boundary



The timeline represents an analytical reconstruction based on the available lab telemetry.



Correlation between events is treated as supporting evidence. A shared source address or temporal proximity alone is not considered sufficient to prove that all observed events were caused by the same actor.

