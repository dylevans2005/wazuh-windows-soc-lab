# Failed Windows Login Detection Report

## Summary

This report documents a failed Windows login detection test performed in a local Wazuh SIEM lab.

A Windows 11 endpoint was connected to Wazuh using the Wazuh agent. Incorrect password attempts were intentionally performed to generate authentication failure events. Wazuh successfully detected the activity and displayed alerts in the Threat Hunting dashboard.

---

## Environment

| Component | Details |
|---|---|
| SIEM | Wazuh |
| Virtualisation | VirtualBox |
| Endpoint OS | Windows 11 |
| Agent Name | DyIOmni7 |
| Detection Type | Failed Windows login |
| Alert Source | Windows Event Logs |

---

## Test Performed

The test involved intentionally entering an incorrect Windows password multiple times on the monitored Windows endpoint.

The purpose of the test was to confirm that Wazuh could:

- receive authentication-related Windows logs
- generate alerts for failed login activity
- display alerts in Threat Hunting
- provide useful fields for investigation

---

## Alert Details

| Field | Value |
|---|---|
| Rule Description | Logon Failure - Unknown user or bad password |
| Rule ID | 60122 |
| Rule Level | 5 |
| Agent Name | DyIOmni7 |
| Alert Type | Failed login |

---

## Screenshots

### Failed Login Alerts

![Failed Login Alerts](../screenshots/failed-login/03-failed-login-alerts.png)

### Alert Document Details

![Alert Details](../screenshots/failed-login/04-alert-document-details.png)

---

## Analysis

The alert indicates that a login attempt failed because of either an unknown user or an incorrect password.

This activity was intentionally generated in a controlled lab environment. Wazuh successfully collected the Windows authentication event from the endpoint and displayed it as a security alert.

In a real SOC environment, repeated failed login alerts could indicate password guessing, brute-force attempts, unauthorised access attempts, or user account issues.

---

## Outcome

The test was successful.

Wazuh detected the failed Windows login activity and displayed the relevant alerts in Threat Hunting. This confirms that the endpoint was connected correctly and that Wazuh was collecting authentication-related Windows logs.

---

## Recommended Response

In a real environment, a SOC analyst could respond by:

- checking whether the failed attempts were expected or suspicious
- reviewing the target username
- checking the number of failed attempts
- identifying whether the activity came from a local or remote source
- comparing the event with successful login activity
- escalating the alert if repeated failures occurred across multiple accounts or systems

---

## Skills Demonstrated

- SIEM alert investigation
- Windows authentication log analysis
- Endpoint monitoring
- Alert triage
- Basic incident documentation
- SOC-style reporting
