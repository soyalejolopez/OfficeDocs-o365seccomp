---
title: Monitor and report security status
description: Describes Microsoft 365 Secure Score, how details are calculated, and what security admins can expect using it.
keywords: security, malware, Microsoft 365, M365, secure score, security center, improvement actions
ms.prod: w10
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance  
ms.topic: article
---

# Monitor and report security status in Microsoft 365 security center

The Microsoft 365 security center provides at a glance summary of protection and security status across your Microsoft 365 environment.

Security center includes a Monitoring & reports section that features a host of cards covering a variety of areas that security analysts and administrators track as part of their day-to-day operations. On drill-down, cards provide detailed reports and, in some cases, management options.

## Customize views

By default, monitoring and report cards are grouped into these categories:
  
* **Identities** – user accounts and credentials
* **Data** – email and document contents
* **Devices** – computers, mobile phones, and other devices
* **Apps** – programs and attached online services
* **Infrastructure** – network infrastructure, both cloud and on-premises

Switch to Group by topic, to rearrange the cards and group them into the following:

* **Risk** – cards that highlight entities, such as accounts and devices, that might be at risk. These cards also highlight possible sources of risk, such as new threat campaigns and privileged cloud apps  
* **Detection trends** – cards that highlight new threat detections, anomalies, and policy violations
* **Configuration and health** – cards that cover the configuration and deployment of security controls, including device onboarding states to management services
* **Other** – all other cards not categorized under other topics

## Monitor and report identities

You can monitor the identities in your organization and keep track of suspicious or risky behaviors. In the Identities category of Monitoring & reports, you can track:

* Users with the most detected anomalies
* How many users are reported at risk by conditional access policies
* The number of global admins in your org

![Identities category of monitoring & reports page](./media/security-docs/identities.png)

For users with specific detections, you can explore the specific alert and investigate in Windows Defender security center. Detections include anomalies such as users who sign in from unfamiliar locations. For a complete set of risk events, see [Azure Active Directory risk events](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-risk-events).

## Monitor and report data

The Data category helps track user activity that could lead to unauthorized data disclosure. These are the rework of existing Office 365 DLP policy reports plus a 3rd party DLP policy match report. You can see:

* Users who share the most files from cloud apps
* How many DLP policy matches occurred
* How many DLP policies overrides or false positives are reported
* How many DLP policy matches happened in 3rd party cloud services via Microsoft Cloud App Security

![Data category of monitoring & reports page](./media/security-docs/data.png)

## Monitor devices

Keep your devices secure, up-to-date, and spot potential threats in the Microsoft 365 security center.

### View device alerts

Get up-to-date alerts about breach activity and other threats on your devices from Windows Defender ATP (available with an E5 license). Microsoft 365 security center has several cards that allow you to effectively monitor these alerts at a high-level, depending on your preferred workflow.

#### Monitor high-impact alerts

Each Windows Defender ATP alert has a corresponding severity—high, medium, low, or informational—that indicates its potential impact to your network if left unattended.  

Use the **Device alert severity** card to focus specifically on alerts that are more severe and might require immediate response. From this card, you can view more information on the Windows Defender Security Center portal.

![Device alerts severity card](./media/security-docs/device-alerts-severity.png)

#### Understand sources of alerts

Windows Defender ATP leverages data from a broad range of security sensors and intelligence sources to generate alerts. For example, it can use detection information from Windows Defender Antivirus and third-party antimalware, as well as your own custom threat intelligence provided through the web service API.

The **Device alert detection** sources card shows the distribution of alerts by source. This card can help you track activity related to certain sources, particularly your custom sources. You can also use this to focus on alerts coming from sensors that are not configured to automatically block malicious activity or components.

![Device alert detection sources card](./media/security-docs/device-alert-detection-sources.png)

From this card, you can view more information on the Windows Defender Security Center portal.

#### Understand the types of threats that trigger alerts

Windows Defender ATP sorts each alert into a category representing a certain stage in the attack chain or a type of threat component. For example, detected threat activity might be categorized into “lateral movement” to indicate that the activity involved an attempt to reach other devices on the network and has likely occurred after attackers have gained an initial foothold. When detected, a threat component might either be classified broadly as “malware” or more specifically as “ransomware”, “credential stealing” or other types of malicious or unwanted software.

The **Device threat categories** card shows the distribution of alerts into these categories. You can use this information to identify threat activity, such as attempts at credential theft, which can have more significant impact compared to attempts at social engineering, for example. You can also use this to monitor for potentially destructive threats like ransomware.

![Device alert detection sources card](./media/security-docs/device-threat-categories.png)

#### Monitor active alerts

The **Device alert status card** indicates the number of alerts that have not been resolved and might require attention. From this card, you can view more information on the Windows Defender Security Center portal.

#### Monitor classification of resolved alerts

When resolving a Window Defender ATP alert, your security staff can specify whether an alert has been verified as:

* A true alert that identifies actual breach activity or threat components
* A false alert that has incorrectly detected normal activity

The **Device alert classification** card shows whether your resolved alerts have been classified as true or false alerts. From this card, you can view more information on the Windows Defender Security Center portal.

Note: In some cases, classification information is unavailable for certain alerts.

#### Monitor determination of resolved alerts

In addition to classifying whether an alert is true or false during resolution, your security staff can provide a determination, indicating the type of normal or malicious activity that was found while validating the alert.

The **Device alert determination** card shows the determination provided for each alert, specifically:

* APT** – advanced persistent threat, indicating that the detected activity or threat component is part of a sophisticated breach designed to gain a foothold in the affected network  
* **Malware** – malicious file or code
* **Security personnel** – normal activity performed by security staff
* **Security testing** – activity or components designed to simulate actual threats and expected to trigger security sensors and generate alerts
* **Unwanted software** – apps and other software that are not considered malicious, but otherwise violate policy or acceptable use standards
* **Others** – any other determination that does not fall under the provided types

From this card, you can view more information in Windows Defender security center.

#### Understand which devices are at risk

**Device protection** shows the risk level for devices. The risk level is based on factors such as the type and severity of alerts on the device.

### Monitor and report status of Intune-managed devices

The following monitoring and reports contain data from devices enrolled in Intune. Data from unenrolled devices is not included. Only Global Administrators can view these cards.

Intune enrolled device data includes:

* Device compliance
* Devices with active malware
* Types of malware on devices
* Malware on devices
* Devices with malware detections
* Users with malware detections

#### Monitor device compliance

**Device compliance** shows how many devices that are enrolled in Intune comply with configuration policies.  

#### Discover devices with malware detections

**Device malware detections** provides the number of Intune enrolled devices with malware that have not been fully resolved due to pending actions—a restart, a full scan or manual user actions—or if the remediation action did not complete successfully.

#### Understand the types of malware detected

**Types of malware on devices** shows different kinds of malware that have been detected on devices enrolled in Intune. You can investigate each type in Microsoft 365 security center.

#### Understand the specific malware detected on your devices

**Malware on devices** provides a list of the specific malware detected on your devices.

#### Understand which devices have the most malware

**Devices with malware detections** shows which devices have the most malware detections. In Microsoft 365 security center, you can investigate whether malware is active, who uses the device, and its management status in Intune.

#### Understand which users have devices with the most malware

**Users with malware detections** shows users with devices that had the most malware detections. In Microsoft 365 security center, you can see how many devices are assigned to each user and more information about each device and the type of malware.

### Monitor and manage ASR rule deployment and detections

[Attack Surface Reduction (ASR) rules](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) help prevent actions and apps that are typically used by exploit-seeking malware to infect machines. These rules control when and how executables can run. For example, you can prevent JavaScript or VBScript from launching a downloaded executable, block Win32 API calls from Office macros, or block processes that run from USB drives.

The **Attack surface reduction rules** card provides an overview of the deployment of rules across your devices.

The top bar on the card shows the total number of devices that are in the following deployment modes:

* **Block mode** – devices with at least one rule configured to block detected activity 
* **Audit mode** – devices with no rules set to block detected activity, but has at least one rule set to audit detected activity  
* **Off** – devices with all ASR rules turned off

The lower part of this card shows settings by rule across your devices. Each bar indicates the number of devices that are set to block or audit detection or have the rule completely turned off.

#### View ASR detections

To view detailed information about ASR rule detections in your network, select **View detections** on the **Attack surface reduction rules** card. The **Detections** tab in the detailed report page will open.

The chart at the top of the page shows detections over time stacking detections that were either blocked or audited. The table at the bottom lists the most recent detections. Use the following information on the table to understand the nature of the detections:

* **Detected file** – the file, typically a script or a document, whose contents triggered the suspected attack activity
* **Rule** – name describing the attack activities the rule is designed to catch. Read about existing ASR rules
* **Source app** – the application that loaded or executed content triggering the suspected attack activity. This could be a legitimate application, such as web browser, an Office application, or a system tool like PowerShell
* **Publisher** – the vendor that released the source app

#### Review device ASR rule settings

In the **Attack surface reduction rules** report page, go to the **Configuration** tab to review rule settings for individual devices. Select a device to get detailed information about whether each rule is in block mode, audit mode, or turned off entirely.

Microsoft Intune provides management functionality for your ASR rules. If you want to update your settings, select **Get started** under **Configure devices** in the tab to open device management on Intune.

#### Exclude files from ASR rules

By excluding files from detections, you can prevent unwanted false positive detections and more confidently deploy attack surface reduction rules in block mode.

While file exclusions for attack surface reduction rules are managed on Microsoft Intune, Microsoft 365 security center provides an analysis tool to help you understand the files that are triggering detections. It also helps collect the names of the files you might want to exclude.

To start analyzing detections and collecting files for exclusion, go to the **Add exclusions** tab in the **Attack surface reduction rules** report page.

The table lists all the file names detected by your attack surface reduction rules. Once you select a file or multiple files, you can review the impact of adding those files to your exceptions: 

* The reduction in the total number of detections
* The reduction in the total number of devices affected by the detections

To get a list of the selected files with their full paths for exclusion, select **Get exclusion paths**.

For more information about exclusions and detailed instructions about how to add them, read [Troubleshoot attack surface reduction rules](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-exploit-guard/troubleshoot-asr).

### Monitor and report app status in Microsoft 365 security

These reports provide more insight into how cloud apps are being used in your organization, including what kinds of apps, their level of risk, and alerts.

#### Monitor email accounts at risk

Email protection shows email accounts at risk. You can click an account to investigate further in Windows Defender security center.

#### Monitor app permissions granted by users

**Cloud App Security - OAuth apps** lists apps discovered by Cloud App Security that have been granted permissions by users. Cloud App Security's risk catalog includes over 16,000 apps that are assessed using over 70 risk factors.

The risk factors start from general information, such as the app publisher, to security measures and controls, such as whether the app supports for encryption at rest or provides an audit log of user activity.

#### Monitor cloud app user accounts

**Cloud app accounts for review** lists accounts that may require attention.

#### Understand which cloud apps are used

**Discovered cloud apps (categories)** show what kinds of apps are being used in your organization and links to the Cloud Discovery dashboard in Cloud App Security. For more information, see [Quickstart: Work with discovered apps](https://docs.microsoft.com/cloud-app-security/discovered-apps).  

#### Monitor where users access cloud apps

**Cloud app activity locations** show where users are accessing cloud apps.

#### Monitor health for infrastructure workloads

Infrastructure health shows health status alerts for infrastructure workloads in Azure Security Center.

Azure Security Center provides unified security management and advanced threat protection across on-premises and cloud workloads. You can collect, search, and analyze security data from a variety of sources, including firewalls and other partner solutions.

For more information, see [Azure Security Center Documentation](https://docs.microsoft.com/azure/security-center/).