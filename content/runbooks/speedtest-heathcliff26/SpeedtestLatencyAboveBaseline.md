---
title: SpeedtestLatencyAboveBaseline
description: Troubleshooting for alert SpeedtestLatencyAboveBaseline
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestLatencyAboveBaseline

Ping latency on {{ $labels.instance }} is {{ printf "%.1f" $value }} ms, exceeding 2x its 10-day average.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestLatencyAboveBaseline" %}}

{{% comment %}}

```yaml
alert: SpeedtestLatencyAboveBaseline
expr: |
    speedtest_ping_latency_milliseconds
      >
    avg_over_time(speedtest_ping_latency_milliseconds[10d]) * 2
    and
    speedtest_ping_latency_milliseconds > 10
for: 30m
labels:
    severity: warning
annotations:
    summary: Latency above baseline
    description: |
        Ping latency on {{ $labels.instance }} is {{ printf "%.1f" $value }} ms, exceeding 2x its 10-day average.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestlatencyabovebaseline/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestLatencyAboveBaseline alert is triggered when the ping latency of a speed test exceeds twice its 10-day average and is greater than 10 milliseconds. This alert indicates a potential issue with network connectivity or server performance, which could impact user experience and overall system reliability.

## Impact
The impact of this alert can be significant, as high latency can lead to slower data transfer rates, increased page load times, and decreased user satisfaction. If left unaddressed, this issue could result in:
* Decreased system performance and responsiveness
* Increased user frustration and churn
* Potential losses in revenue or productivity
* Damage to the organization's reputation and brand

## Diagnosis
To diagnose the root cause of the SpeedtestLatencyAboveBaseline alert, follow these steps:
1. **Check network connectivity**: Verify that there are no issues with the network connection, such as outages, congestion, or misconfigurations.
2. **Investigate server performance**: Analyze server logs and metrics to identify any performance issues, such as high CPU usage, memory leaks, or disk bottlenecks.
3. **Review speed test configuration**: Ensure that the speed test is properly configured and calibrated to provide accurate results.
4. **Compare with historical data**: Examine historical latency data to determine if this is an isolated incident or a recurring issue.
5. **Consult with relevant teams**: Collaborate with network, server, and development teams to gather insights and expertise.

## Mitigation
To mitigate the effects of the SpeedtestLatencyAboveBaseline alert, consider the following steps:
1. **Implement network optimizations**: Apply network tweaks, such as Quality of Service (QoS) policies, traffic shaping, or packet prioritization, to improve data transfer efficiency.
2. **Upgrade server hardware or configuration**: Enhance server capabilities by adding resources, such as CPU, memory, or storage, or optimizing server settings for better performance.
3. **Adjust speed test settings**: Fine-tune speed test parameters, such as test frequency, sample size, or timeout values, to reduce the impact of latency on test results.
4. **Apply content delivery network (CDN) or caching**: Leverage CDNs or caching mechanisms to reduce the distance between users and content, minimizing latency and improving overall performance.
5. **Schedule maintenance and monitoring**: Regularly inspect and maintain network and server infrastructure to prevent similar issues from arising in the future.