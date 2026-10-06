&#x20;Authentication Monitoring Dashboard



&#x20;Purpose



This dashboard provides a visual overview of successful and failed Windows authentication activity observed in the Splunk environment.



&#x20;Data Source



Windows Security logs.



The investigation uses:



\- Event ID 4625 — failed logon

\- Event ID 4624 — successful logon



&#x20;Monitoring Objective



The dashboard helps an analyst identify:



\- The volume of failed authentication attempts

\- Successful authentication activity

\- Changes in authentication activity over time

\- Patterns that may warrant further investigation



&#x20;Investigation Use



A high number of failed logons from the same source can indicate possible brute-force activity.



A successful logon occurring after repeated failures can be used as an investigation lead and should be examined together with:



\- Source IP

\- Username

\- Timestamp

\- Host

\- Related network activity



&#x20;Analyst Workflow





Authentication Events

&#x20;       ↓

Success / Failure Comparison

&#x20;       ↓

Identify Abnormal Patterns

&#x20;       ↓

Review Source and User

&#x20;       ↓

Correlate With Other Telemetry

&#x20;       ↓

Investigate



Evidence



The project documentation includes a Splunk dashboard showing logon success versus failure as part of the SOC investigation.



Limitation



The dashboard is a monitoring and investigation aid. A successful login following failed attempts does not, by itself, prove account compromise.

