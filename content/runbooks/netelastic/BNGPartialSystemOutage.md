---
title: BNGPartialSystemOutage
description: Troubleshooting for alert BNGPartialSystemOutage
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# BNGPartialSystemOutage

All BNG instances in system {{ $labels.system }} are down. Customers will experience an outage.

<details>
  <summary>Alert Rule</summary>

{{% rule "netelastic/netelastic.yml" "BNGPartialSystemOutage" %}}

{{% comment %}}

```yaml
alert: BNGPartialSystemOutage
expr: "( (\n  sum(up{job=\"netelastic\",system!=\"None\"}) by (system) > 0\n)\nand\n(\n  sum(up{job=\"netelastic\",system!=\"None\"}) by (system)\n  <\n  count(up{job=\"netelastic\",system!=\"None\"}) by (system)\n)) or (            \n(\n  sum(probe_success{job=\"blackbox\",system!=\"None\",instance=~\".*bng.*\"}) by (system) > 0\n)\nand\n(\n  sum(probe_success{job=\"blackbox\",system!=\"None\",instance=~\".*bng.*\"}) by (system)\n  <\n  count(probe_success{job=\"blackbox\",system!=\"None\",instance=~\".*bng.*\"}) by (system)\n) ) \n"
for: 5m
labels:
    severity: critical
annotations:
    summary: BNG outage in system {{ $labels.system }}
    description: |
        All BNG instances in system {{ $labels.system }} are down. Customers will experience an outage.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/netelastic/bngpartialsystemoutage/

```

{{% /comment %}}

</details>


## Meaning
The BNGPartialSystemOutage alert rule is triggered when there is a partial outage of BNG (Broadband Network Gateway) instances in a system. This can be caused by one or more BNG instances being down, resulting in a disruption of service to customers. The alert is critical and indicates that immediate attention is required to resolve the issue.

## Impact
The impact of this alert is significant, as it affects the availability of broadband services to customers. When BNG instances are down, customers may experience interrupted or lost service, leading to frustration and potential loss of business. The severity of the alert is critical, indicating that the issue should be addressed promptly to minimize the impact on customers and the business.

## Diagnosis
To diagnose the issue, the following steps can be taken:
1. **Check the Prometheus dashboard**: Review the Prometheus dashboard to see which BNG instances are down and which system is affected.
2. **Verify instance status**: Use the `up` metric to verify the status of the BNG instances in the affected system.
3. **Check blackbox probe results**: Review the `probe_success` metric for the blackbox job to see if the BNG instances are responding to probes.
4. **Investigate system logs**: Check the system logs for any errors or issues that may be related to the BNG instance outage.
5. **Contact relevant teams**: Reach out to the network operations team and other relevant teams to gather more information about the issue.

## Mitigation
To mitigate the issue, the following steps can be taken:
1. **Restart affected BNG instances**: Attempt to restart the down BNG instances to see if they will recover.
2. **Check for configuration issues**: Verify that the BNG instances are configured correctly and that there are no issues with the configuration.
3. **Investigate network connectivity**: Check the network connectivity to the BNG instances to ensure that there are no issues with the network.
4. **Apply fixes or patches**: If the issue is due to a known bug or vulnerability, apply the relevant fixes or patches to the BNG instances.
5. **Escalate to vendor support**: If the issue cannot be resolved internally, escalate the issue to the vendor support team for further assistance.