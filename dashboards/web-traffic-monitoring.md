&#x20;Web Traffic Monitoring Dashboard



&#x20;Purpose



This dashboard provides visibility into web request activity observed in the Splunk environment and supports investigation of suspicious request patterns.



&#x20;Data Source



Apache access logs.



The investigation focuses on:



\- Request paths

\- HTTP status codes

\- Source addresses

\- Request frequency

\- Activity over time



&#x20;Monitoring Objective



The dashboard helps an analyst identify:



\- Repeated requests to sensitive paths

\- High-frequency HTTP 404 responses

\- Suspicious request patterns

\- Changes in web activity over time



&#x20;Suspicious Paths



The investigation examined requests targeting:



\- `/admin`

\- `/login`

\- `/phpmyadmin`



Suspicious request strings such as `union` and `../` were also investigated.



&#x20;Time-Based Analysis



Web request activity can be grouped into time intervals to identify periods of increased suspicious activity.



Example SPL:





index=\* ("union" OR "../" OR "/admin" OR "/phpmyadmin")

| timechart span=1h count



Analyst Workflow



Apache Web Events

&#x20;       ↓

Filter Suspicious Requests

&#x20;       ↓

Analyze Status Codes

&#x20;       ↓

Group Activity Over Time

&#x20;       ↓

Identify Activity Spikes

&#x20;       ↓

Correlate With Other Telemetry



Investigation Use



The dashboard supports investigation of reconnaissance and suspicious web activity.



A high frequency of requests or repeated access to sensitive paths should be examined together with timestamps, source addresses, HTTP status codes, and related firewall or authentication events.



Evidence



The project documentation includes a Splunk SIEM dashboard and a separate time-based analysis of suspicious web requests.



Limitation



Suspicious request patterns indicate activity requiring investigation. They do not independently establish successful exploitation or system compromise.

