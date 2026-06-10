---
title: SpeedtestDownloadBelowBaseline
description: Troubleshooting for alert SpeedtestDownloadBelowBaseline
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestDownloadBelowBaseline

Download throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps, which is more than 25% below its 10-day average.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestDownloadBelowBaseline" %}}

{{% comment %}}

```yaml
alert: SpeedtestDownloadBelowBaseline
expr: |
    speedtest_download_megabits_per_second
      <
    avg_over_time(speedtest_download_megabits_per_second[10d]) * 0.75
for: 1h
labels:
    severity: warning
annotations:
    summary: Download throughput below baseline
    description: |
        Download throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps, which is more than 25% below its 10-day average.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestdownloadbelowbaseline/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestDownloadBelowBaseline alert is triggered when the download throughput of a speedtest instance falls below 75% of its 10-day average. This alert is designed to detect significant deviations in download speeds, which could indicate issues with network connectivity, server performance, or other underlying infrastructure problems.

## Impact
The impact of this alert can vary depending on the specific use case and the dependence on fast and reliable download speeds. Potential consequences include:
* Slower than expected download times for users, potentially leading to a poor user experience
* Increased latency and delays in data transfer, which can affect real-time applications and services
* Potential issues with data integrity and consistency, particularly if the reduced download speeds are causing errors or timeouts
* Negative impact on business operations and revenue, especially if the affected system is critical to business functions

## Diagnosis
To diagnose the issue, follow these steps:
1. **Verify the alert details**: Review the alert notification to understand the affected instance, the current download speed, and the baseline average.
2. **Check network connectivity**: Investigate network connectivity issues, such as packet loss, latency, or congestion, that could be causing the reduced download speeds.
3. **Inspect server performance**: Examine server performance metrics, like CPU usage, memory utilization, and disk I/O, to identify potential bottlenecks.
4. **Analyze speedtest data**: Review historical speedtest data to determine if the issue is intermittent or persistent.
5. **Consult with relevant teams**: Collaborate with network, server, and application teams to gather information and identify potential causes.

## Mitigation
To mitigate the issue, consider the following steps:
1. **Investigate and address network issues**: Resolve any network connectivity problems, such as packet loss or congestion, that may be contributing to the reduced download speeds.
2. **Optimize server performance**: Adjust server configurations, such as increasing resources or optimizing settings, to improve performance and reduce bottlenecks.
3. **Verify speedtest configuration**: Ensure that the speedtest instance is properly configured and functioning as expected.
4. **Implement monitoring and alerting**: Set up additional monitoring and alerting to quickly detect similar issues in the future.
5. **Schedule maintenance and upgrades**: Plan and perform regular maintenance and upgrades to ensure the affected system remains performant and reliable.