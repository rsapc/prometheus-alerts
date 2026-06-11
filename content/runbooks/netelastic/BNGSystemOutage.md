---
title: BNGSystemOutage
description: Troubleshooting for alert BNGSystemOutage
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# BNGSystemOutage

All BNG instances in system {{ $labels.system }} are down. Customers will experience an outage.

<details>
  <summary>Alert Rule</summary>

{{% rule "netelastic/netelastic.yml" "BNGSystemOutage" %}}

{{% comment %}}

```yaml
alert: BNGSystemOutage
expr: (avg(up{job="netelastic",system!="None"}) by (system) == 0) or ( avg(probe_success{job="blackbox",system!="None",instance=~".*bng.*"}) == 0)
for: 5m
labels:
    severity: critical
annotations:
    summary: BNG outage in system {{ $labels.system }}
    description: |
        All BNG instances in system {{ $labels.system }} are down. Customers will experience an outage.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/netelastic/bngsystemoutage/

```

{{% /comment %}}

</details>


## Meaning
The BNGSystemOutage alert is triggered when all BNG instances in a system are down, indicated by a 5-minute average of zero for the `up` metric or the `probe_success` metric for BNG-related instances. This alert is critical, as it signifies a complete outage of BNG services in the affected system, impacting customer experience.

## Impact
The impact of this alert is significant, as it affects the availability of BNG services to customers. When all BNG instances in a system are down, customers will experience an outage, leading to potential revenue loss, damage to reputation, and decreased customer satisfaction. Prompt mitigation is essential to minimize the duration and impact of the outage.

## Diagnosis
To diagnose the issue, the following steps can be taken:
1. **Verify system and instance status**: Check the Prometheus dashboard for the `up` and `probe_success` metrics to confirm that all BNG instances in the system are indeed down.
2. **Investigate system logs**: Examine system logs for any error messages or unusual activity that may indicate the cause of the outage.
3. **Check network connectivity**: Verify that there are no network connectivity issues that could be preventing the BNG instances from functioning correctly.
4. **Review recent changes**: Investigate any recent changes or updates made to the system or instances that may have contributed to the outage.

## Mitigation
To mitigate the BNGSystemOutage, the following steps can be taken:
1. **Restore BNG instances**: Attempt to restart or restore the BNG instances to bring them back online.
2. **Resolve underlying issues**: Address any underlying issues or errors that may have caused the outage, such as network connectivity problems or system configuration issues.
3. **Implement temporary workaround**: If necessary, implement a temporary workaround to provide minimal BNG services to customers until the primary instances can be restored.
4. **Monitor system stability**: Closely monitor the system and instances after mitigation to ensure stability and prevent future outages.
5. **Perform post-outage analysis**: Conduct a post-outage analysis to identify the root cause of the issue and implement measures to prevent similar outages in the future.