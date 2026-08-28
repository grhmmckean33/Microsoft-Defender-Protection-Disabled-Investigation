<div align="center">

![Microsoft Defender Protection Disabled](assets/banner.svg)

# Microsoft Defender Protection Disabled

**Splunk, Defender and Sysmon correlation around endpoint security-control changes**

[![Live Case Study](https://img.shields.io/badge/Live%20Case%20Study-Open-22c55e?style=for-the-badge)](https://grhmmckean33.github.io/soc-defender-protection-disabled-investigation/) [![PDF Report](https://img.shields.io/badge/PDF%20Report-View-dc2626?style=for-the-badge)](report/SOC_Investigation_Report_Defender_Protection_Disabled.pdf)

</div>

## Case study overview

A SOC investigation into Microsoft Defender Real-time Protection being disabled. The investigation correlated Windows Security activity, Defender Operational events and Sysmon telemetry, then analysed later execution of Defender Control v2.1 without incorrectly attributing it as the cause of the earlier disable event.

| Area | Detail |
| --- | --- |
| Severity | **Medium** |
| Assessment | **Suspicious - User-associated changes; no confirmed compromise** |
| Environment | Kerning City Dental (KCD) |
| MITRE ATT&CK | T1562.001 - Impair Defenses: Disable or Modify Tools |
| Full case study | **[View GitHub Pages site](https://grhmmckean33.github.io/soc-defender-protection-disabled-investigation/)** |
| Investigation report | **[Open PDF](report/SOC_Investigation_Report_Defender_Protection_Disabled.pdf)** |

## Key findings

- Defender Real-time Protection was disabled at 18:40:59 UTC during an active KCD-Contractor session.
- Windows Security components and Defender-related service/configuration changes were observed immediately around the state change.
- dControl.exe was deliberately executed by KCD-Contractor approximately two minutes after the original disable event and later obtained SYSTEM-level execution.
- Hash-based OSINT identified the binary as Defender Control v2.1; repeated historical use was found, but organisational authorisation could not be established.

## Investigation approach

- Validated the Splunk detection and recovered the original Defender event.
- Correlated Defender Operational and Sysmon telemetry around the protection change.
- Performed timing analysis to avoid incorrectly blaming dControl for the earlier Event ID 5001.
- Used file-hash OSINT to identify the utility while keeping malicious intent unproven.

## SOC skills demonstrated

`Splunk investigation`, `Defender Operational analysis`, `Sysmon correlation`, `User/session attribution`, `Hash and OSINT validation`, `Cautious causal analysis`

## Report structure

The full PDF report contains the investigation findings, evidence-led summary, timeline where applicable, 5Ws and 1H, observed or incident-associated indicators, assessment, recommendations and documented investigation limitations.

---

**Prepared by Graham McKean**  
SOC investigation portfolio case study. External indicators are defanged where applicable.
