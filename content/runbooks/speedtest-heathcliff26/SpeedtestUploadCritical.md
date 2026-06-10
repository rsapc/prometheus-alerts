---
title: SpeedtestUploadCritical
description: Troubleshooting for alert SpeedtestUploadCritical
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestUploadCritical

Upload throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestUploadCritical" %}}

{{% comment %}}

```yaml
alert: SpeedtestUploadCritical
expr: speedtest_upload_megabits_per_second < 500
for: 15m
labels:
    severity: critical
annotations:
    summary: Severely degraded upload throughput
    description: |
        Upload throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestuploadcritical/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestUploadCritical alert is triggered when the upload throughput falls below 500 megabits per second for a duration of 15 minutes. This alert indicates a severely degraded upload performance, which may be caused by various factors such as network congestion, hardware issues, or configuration problems.

## Impact
The impact of this alert can be significant, as it may affect the overall performance and reliability of the system or network. Severely degraded upload throughput can lead to delays, timeouts, and errors in data transmission, which can have cascading effects on dependent systems or applications. This can result in decreased productivity, increased latency, and potential data loss.

## Diagnosis
To diagnose the issue, the following steps can be taken:
1. **Check network configuration**: Verify that the network settings are correct and that there are no misconfigurations or conflicts.
2. **Monitor network traffic**: Analyze network traffic patterns to identify potential bottlenecks or congestion points.
3. **Inspect hardware**: Check the condition and performance of network hardware, such as routers, switches, and interfaces.
4. **Review system logs**: Examine system logs to identify any error messages or warnings related to network or system performance.
5. **Run speed tests**: Conduct additional speed tests to confirm the upload throughput and identify any variations or fluctuations.

## Mitigation
To mitigate the issue, the following steps can be taken:
1. **Optimize network configuration**: Adjust network settings to optimize performance and reduce congestion.
2. **Implement Quality of Service (QoS)**: Configure QoS policies to prioritize critical traffic and ensure sufficient bandwidth.
3. **Upgrade or replace hardware**: Consider upgrading or replacing network hardware to improve performance and capacity.
4. **Implement traffic shaping**: Use traffic shaping techniques to manage bandwidth allocation and reduce congestion.
5. **Contact ISP or network provider**: If the issue persists, contact the Internet Service Provider (ISP) or network provider to report the problem and request assistance.