---
title: SpeedtestDownloadCritical
description: Troubleshooting for alert SpeedtestDownloadCritical
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestDownloadCritical

Download throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestDownloadCritical" %}}

{{% comment %}}

```yaml
alert: SpeedtestDownloadCritical
expr: speedtest_download_megabits_per_second < 500
for: 15m
labels:
    severity: critical
annotations:
    summary: Severely degraded download throughput
    description: |
        Download throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestdownloadcritical/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestDownloadCritical alert is triggered when the download speed of a speed test falls below 500 megabits per second for a duration of 15 minutes. This indicates a severely degraded download throughput, which can significantly impact the performance and usability of network-dependent applications.

## Impact
The impact of this alert can be significant, as a severely degraded download throughput can:
* Affect the performance of critical applications and services
* Lead to increased latency and packet loss
* Impact user experience and productivity
* Potentially cause financial losses or reputational damage
* Affect the overall reliability and availability of the network

## Diagnosis
To diagnose the root cause of the SpeedtestDownloadCritical alert, the following steps can be taken:
* Check the speed test logs to identify any patterns or trends in the download throughput
* Verify that the speed test is configured correctly and that the test is being run against a reliable server
* Check the network configuration and topology to identify any potential bottlenecks or issues
* Monitor the network traffic to identify any suspicious or abnormal activity
* Check the system resources (e.g., CPU, memory, disk space) to ensure that they are not overloaded

## Mitigation
To mitigate the SpeedtestDownloadCritical alert, the following steps can be taken:
* Check the network configuration and make any necessary adjustments to optimize the download throughput
* Contact the ISP or network provider to report the issue and request assistance in resolving it
* Consider upgrading the network infrastructure or hardware to improve performance
* Implement quality of service (QoS) policies to prioritize critical traffic and ensure that it is not impacted by the degraded download throughput
* Monitor the download throughput closely and adjust the alert thresholds as needed to prevent false positives or false negatives.