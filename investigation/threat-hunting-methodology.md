&#x20;Threat Hunting Methodology



&#x20;1. Establish the Investigation Hypothesis



The investigation begins by identifying an activity pattern that may indicate reconnaissance, suspicious web activity, or unauthorized authentication.



Examples include:



\- Repeated requests to sensitive web paths

\- High-frequency HTTP 404 responses

\- Repeated connection attempts

\- Multiple failed authentication attempts

\- Successful authentication following failed attempts



&#x20;2. Analyze Individual Data Sources



Each telemetry source is first examined independently.



&#x20;Apache



Review:



\- Request paths

\- HTTP status codes

\- Source IP addresses

\- Request frequency

\- Suspicious strings and URI patterns



&#x20;Firewall



Review:



\- Source addresses

\- Destination ports

\- Allowed and blocked connections

\- Event frequency

\- Event timing



&#x20;Windows Security Logs



Review:



\- Event ID 4625 — failed logon

\- Event ID 4624 — successful logon

\- User

\- Source address

\- Timestamp



&#x20;3. Identify Suspicious Patterns



Searches are used to isolate activity that requires additional investigation.



Examples:



\- `/admin`

\- `/login`

\- `/phpmyadmin`

\- `union`

\- `../`

\- Repeated authentication failures



&#x20;4. Correlate Events



Relevant timestamps and source addresses are compared across Apache, firewall, and Windows telemetry.



The purpose is to determine whether activity across different data sources forms a consistent sequence.



&#x20;5. Reconstruct the Timeline



Events are arranged chronologically to understand the progression of observed activity.



A typical investigation sequence may include:





Network connection activity

&#x20;       ↓

Web reconnaissance

&#x20;       ↓

Repeated authentication failures

&#x20;       ↓

Successful authentication

&#x20;       ↓

Further investigation



This represents an investigative hypothesis rather than proof that every event originated from the same attacker.



6\. Assess the Evidence



The analyst distinguishes between:

\- Directly observed telemetry

\- Correlated indicators

\- Analyst interpretation

\- Unconfirmed hypotheses



Temporal proximity or a shared source address is treated as supporting evidence rather than conclusive proof of causation.



7\. Recommend Defensive Controls



Depending on the findings, recommended controls include:

\- Account lockout policies

\- Strong authentication and MFA

\- Restricted access to administrative web paths

\- Firewall restrictions

\- Continuous authentication monitoring

\- SIEM alerting

\- Regular patching



Investigation Principle



The objective is not simply to find a suspicious event. The objective is to determine:

1\. What happened?

2\. When did it happen?

3\. Which telemetry supports the finding?

4\. What activity can be correlated?

5\. What remains unconfirmed?

6\. What defensive action should be considered?

