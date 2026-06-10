---
title: FreeRadiusPartialSystemOutage
description: Troubleshooting for alert FreeRadiusPartialSystemOutage
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# FreeRadiusPartialSystemOutage

Some FreeRADIUS instances in system {{ $labels.system }} are down, but at least one instance remains available.

<details>
  <summary>Alert Rule</summary>

{{% rule "freeradius/freeradius-apc.yml" "FreeRadiusPartialSystemOutage" %}}

{{% comment %}}

```yaml
alert: FreeRadiusPartialSystemOutage
expr: |
    (
      sum(freeradius_up{system!="None"}) by (system) > 0
    )
    and
    (
      sum(freeradius_up{system!="None"}) by (system)
      <
      count(freeradius_up{system!="None"}) by (system)
    )
for: 5m
labels:
    severity: warning
annotations:
    summary: FreeRADIUS partial outage in system {{ $labels.system }}
    description: |
        Some FreeRADIUS instances in system {{ $labels.system }} are down, but at least one instance remains available.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/freeradius-apc/freeradiuspartialsystemoutage/

```

{{% /comment %}}

</details>


## Meaning
The FreeRadiusPartialSystemOutage alert is triggered when at least one FreeRADIUS instance in a system is down, but not all instances are down. This indicates a partial outage in the system, where some users or services may be affected, but others remain operational. The alert is raised when the number of available FreeRADIUS instances in a system is greater than 0, but less than the total number of instances in that system.

## Impact
The impact of a FreeRadiusPartialSystemOutage alert can be significant, as it may affect user authentication, network access, or other critical services that rely on FreeRADIUS. The partial outage can lead to:
* Intermittent or failed authentication attempts
* Disrupted network connectivity
* Increased latency or errors in dependent services
* Potential security risks if the affected instances are not properly secured

## Diagnosis
To diagnose the issue, follow these steps:
1. **Identify the affected system**: Check the alert label `system` to determine which system is experiencing the partial outage.
2. **Verify instance status**: Use the `freeradius_up` metric to check the status of individual instances in the affected system.
3. **Check instance logs**: Inspect the logs of the affected instances for any error messages or indications of what may be causing the outage.
4. **Investigate potential causes**: Look into potential causes such as:
	* Network connectivity issues
	* Configuration errors
	* Resource constraints (e.g., CPU, memory)
	* Software or hardware failures

## Mitigation
To mitigate the issue, follow these steps:
1. **Investigate and address the root cause**: Based on the diagnosis, address the underlying cause of the outage.
2. **Restart or recover affected instances**: Attempt to restart or recover the affected instances to restore full functionality.
3. **Implement temporary workarounds**: If necessary, implement temporary workarounds to minimize the impact on users or services, such as:
	* Redirecting traffic to available instances
	* Implementing failover mechanisms
	* Increasing resources or capacity
4. **Monitor and verify resolution**: Continuously monitor the system and verify that the issue has been fully resolved and all instances are operational.