---
title: SpeedtestFailed
description: Troubleshooting for alert SpeedtestFailed
#published: true
date: 2023-12-12T21:12:32.022Z
tags: 
  - LGTM
  - generated
editor: markdown
dateCreated: 2020-04-10T18:32:27.079Z
---

# SpeedtestFailed

Speedtest has not completed successfully for at least 15 minutes.

<details>
  <summary>Alert Rule</summary>

{{% rule "speedtest/speedtest-heathcliff26.yml" "SpeedtestFailed" %}}

{{% comment %}}

```yaml
alert: SpeedtestFailed
expr: speedtest_up == 0
for: 15m
labels:
    severity: critical
annotations:
    summary: Speedtest failed
    description: |
        Speedtest has not completed successfully for at least 15 minutes.
    runbook: https://srerun.github.io/prometheus-alerts/runbooks/speedtest-heathcliff26/speedtestfailed/

```

{{% /comment %}}

</details>


## Meaning
The SpeedtestFailed alert is triggered when the `speedtest_up` metric is 0 for at least 15 minutes, indicating that the speed test has not completed successfully. This alert is critical, as it suggests a potential issue with the network or system that is preventing the speed test from running correctly.

## Impact
The impact of this alert is significant, as it may indicate a problem with the network or system that is affecting its performance and reliability. If the speed test is not able to complete successfully, it may be difficult to diagnose and troubleshoot other issues, which could lead to further downtime and disruptions. Additionally, this alert may indicate a problem with the monitoring system itself, which could lead to a loss of visibility into the system's performance and health.

## Diagnosis
To diagnose the issue, the following steps can be taken:
1. Check the speed test logs to see if there are any error messages or indications of what is causing the test to fail.
2. Verify that the speed test is configured correctly and that all necessary dependencies are in place.
3. Check the network and system for any issues that may be affecting the speed test, such as high latency or packet loss.
4. Attempt to run the speed test manually to see if it completes successfully.
5. Check the Prometheus metrics for any other indicators of issues with the system or network.

## Mitigation
To mitigate the issue, the following steps can be taken:
1. Check the speed test configuration and update it if necessary to ensure that it is running correctly.
2. Perform any necessary maintenance or repairs on the network or system to resolve any issues that may be affecting the speed test.
3. Consider implementing additional monitoring or logging to help diagnose and troubleshoot issues with the speed test.
4. If the issue is related to a specific dependency or component, consider updating or replacing it to resolve the issue.
5. Once the issue is resolved, verify that the speed test is completing successfully and that the `speedtest_up` metric is being reported correctly.