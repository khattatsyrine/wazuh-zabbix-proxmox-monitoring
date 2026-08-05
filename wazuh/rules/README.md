# Wazuh Custom Correlation Rule

This folder contains a sanitized version of a custom Wazuh rule created during the monitoring project.

## Purpose

The rule detects repeated Postfix SASL authentication failures occurring within a short period.

A single authentication failure may result from a typing mistake or an outdated password. Several failures in a short period can indicate repeated unauthorized login attempts and therefore require greater attention.

## Rule Logic

| Parameter | Value | Purpose |
|---|---:|---|
| Base rule | `3332` | Identifies a Postfix SASL authentication failure |
| Frequency | `3` | Requires repeated matching events |
| Timeframe | `120` seconds | Defines the correlation period |
| Alert level | `10` | Raises the severity of the correlated event |
| MITRE ATT&CK | `T1110` | Maps the activity to brute-force attempts |

The custom rule uses `if_matched_sid` to correlate alerts already identified by the base Wazuh rule.

```xml
<rule id="100101" level="10" frequency="3" timeframe="120">
  <if_matched_sid>3332</if_matched_sid>
</rule>
