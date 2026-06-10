---
title: SpeedtestHighJitter
description: Troubleshooting for alert SpeedtestHighJitter
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestHighJitter

Jitter on {{ $labels.instance }} is {{ printf "%.1f" $value }} ms.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestHighJitter" %}}

{{% comment %}}

```yaml
alert: SpeedtestHighJitter
expr: speedtest_jitter_latency_milliseconds > 10
for: 15m
labels:
    severity: warning
annotations:
    summary: High jitter detected
    description: |
        Jitter on {{ $labels.instance }} is {{ printf "%.1f" $value }} ms.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtesthighjitter/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestHighJitter alert is triggered when the jitter latency measured by a speed test exceeds 10 milliseconds for a duration of 15 minutes. This indicates that the network connection is experiencing high levels of packet delay variation, which can cause issues with real-time applications such as video conferencing, online gaming, and VoIP calls.

## Impact
High jitter can significantly impact the quality of service (QoS) and user experience, leading to:
* Poor video and audio quality in real-time applications
* Increased packet loss and retransmissions
* Decreased overall network performance
* Potential disruption to critical services and applications

## Diagnosis
To diagnose the issue, follow these steps:
1. **Check network configuration**: Verify that the network configuration is correct and that there are no issues with the underlying infrastructure.
2. **Monitor network traffic**: Analyze network traffic patterns to identify potential sources of jitter, such as high-priority traffic or packet flooding.
3. **Investigate speed test results**: Review the speed test results to determine if the issue is specific to a particular instance or if it's a broader network problem.
4. **Check for hardware or software issues**: Investigate if there are any hardware or software issues with the devices or servers involved in the speed test.

## Mitigation
To mitigate the issue, consider the following steps:
1. **Adjust QoS settings**: Adjust QoS settings to prioritize critical traffic and reduce packet delay variation.
2. **Optimize network configuration**: Optimize network configuration to reduce congestion and ensure proper traffic flow.
3. **Implement traffic shaping**: Implement traffic shaping to limit the amount of bandwidth allocated to non-critical applications.
4. **Perform maintenance and upgrades**: Perform regular maintenance and upgrades to ensure that network devices and servers are running with the latest software and firmware.
5. **Monitor and analyze network performance**: Continuously monitor and analyze network performance to quickly identify and address any issues that may arise.