---
title: SpeedtestUploadBelowBaseline
description: Troubleshooting for alert SpeedtestUploadBelowBaseline
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestUploadBelowBaseline

Upload throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps, which is more than 25% below its 10-day average.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestUploadBelowBaseline" %}}

{{% comment %}}

```yaml
alert: SpeedtestUploadBelowBaseline
expr: |
    speedtest_upload_megabits_per_second
      <
    avg_over_time(speedtest_upload_megabits_per_second[10d]) * 0.75
for: 1h
labels:
    severity: warning
annotations:
    summary: Upload throughput below baseline
    description: |
        Upload throughput on {{ $labels.instance }} is {{ printf "%.0f" $value }} Mbps, which is more than 25% below its 10-day average.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestuploadbelowbaseline/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestUploadBelowBaseline alert is triggered when the upload throughput of a speed test falls below 75% of its 10-day average. This indicates a potential issue with the network or internet connection, which could be affecting the performance and reliability of online services. The alert is classified as a warning, suggesting that the issue is notable but not critical.

## Impact
The impact of this alert can vary depending on the specific use case and requirements of the system or service being monitored. Potential effects include:
* Reduced upload speeds for users, potentially leading to frustrated users and decreased productivity
* Increased latency or errors when uploading data, which could affect real-time applications or services
* Potential issues with cloud-based services or applications that rely on stable and fast upload speeds
* Decreased overall network performance and reliability

## Diagnosis
To diagnose the issue, the following steps can be taken:
1. **Verify the alert**: Check the Prometheus dashboard to confirm that the alert is valid and not a false positive.
2. **Check network configuration**: Review the network configuration and settings to ensure that there are no issues or changes that could be affecting upload speeds.
3. **Monitor system logs**: Check system logs for any error messages or warnings related to network or internet connectivity.
4. **Run additional tests**: Run additional speed tests or network diagnostics to confirm the issue and gather more information.
5. **Check for external factors**: Investigate if there are any external factors, such as ISP outages or maintenance, that could be affecting upload speeds.

## Mitigation
To mitigate the issue, the following steps can be taken:
1. **Investigate and resolve underlying issues**: Identify and resolve any underlying issues with the network or internet connection, such as configuration errors or hardware problems.
2. **Contact ISP or network provider**: If the issue is related to the ISP or network provider, contact their support team to report the issue and request assistance.
3. **Implement QoS policies**: Implement Quality of Service (QoS) policies to prioritize critical traffic and ensure that upload speeds are maintained for essential services.
4. **Upgrade or optimize network infrastructure**: Consider upgrading or optimizing network infrastructure, such as routers or switches, to improve overall network performance and reliability.
5. **Monitor and adjust**: Continuously monitor upload speeds and adjust mitigation strategies as needed to ensure that the issue is resolved and upload speeds are maintained.