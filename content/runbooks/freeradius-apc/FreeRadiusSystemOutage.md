---
title: FreeRadiusSystemOutage
description: Troubleshooting for alert FreeRadiusSystemOutage
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# FreeRadiusSystemOutage

All FreeRADIUS instances in system {{ $labels.system }} are down. Customers will not be able to authenticate.

<details>
  <summary>Alert Rule</summary>

{{% rule "freeradius/freeradius-apc.yml" "FreeRadiusSystemOutage" %}}

{{% comment %}}

```yaml
alert: FreeRadiusSystemOutage
expr: avg(freeradius_up{system!="None"}) by (system) == 0
for: 5m
labels:
    severity: critical
annotations:
    summary: FreeRADIUS outage in system {{ $labels.system }}
    description: |
        All FreeRADIUS instances in system {{ $labels.system }} are down. Customers will not be able to authenticate.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/freeradius-apc/freeradiussystemoutage/

```

{{% /comment %}}

</details>


## Meaning
The FreeRadiusSystemOutage alert is triggered when all FreeRADIUS instances in a specific system are down, indicated by the `freeradius_up` metric averaging to 0 over a 5-minute period. This alert is critical, as it directly affects customer authentication.

## Impact
The impact of this outage is significant, as customers will not be able to authenticate, potentially leading to a loss of service and revenue. This can also lead to a negative user experience, damage to the organization's reputation, and increased support requests.

## Diagnosis
To diagnose the issue, follow these steps:
1. Check the FreeRADIUS server logs for any error messages or exceptions that may indicate the cause of the outage.
2. Verify that the FreeRADIUS servers are properly configured and running.
3. Check the network connectivity between the FreeRADIUS servers and the systems that rely on them for authentication.
4. Review the system's monitoring metrics to see if there are any other related issues or outages.

## Mitigation
To mitigate the issue, follow these steps:
1. **Immediate Action**: Notify the team responsible for maintaining the FreeRADIUS system and request their assistance in resolving the issue.
2. **Root Cause Analysis**: Identify the root cause of the outage and take corrective action to prevent it from happening again in the future.
3. **Temporary Workaround**: If possible, configure a temporary workaround to allow customers to authenticate, such as using an alternative authentication system.
4. **System Recovery**: Once the root cause has been addressed, restart the FreeRADIUS servers and verify that they are functioning correctly.
5. **Post-Incident Review**: Conduct a post-incident review to identify areas for improvement and implement changes to prevent similar outages in the future.