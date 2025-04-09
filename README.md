# Active-Directory-Lab

## Overview

This project demonstrates a realistic Active Directory (AD) environment with integrated log monitoring and threat detection capabilities using Splunk and Atomic Red Team to simulate and monitor security incidents.


### Objectives

-   Install virtual box and set up machines.
-   To set up a fully functional Active Directory environment that mimics a real-world enterprise setup.
-   To implement centralized log monitoring using Splunk Enterprise.
-   To simulate cyberattacks using Atomic Red Team and Crowbar, detect the attacks using splunk.
-   To gain hands-on experience in system administration, security monitoring, and incident detection..

## Installation Guide
<a href="https://github.com/nickagesa/Active-Directory-Lab/blob/main/Installation_Guide.md">Installation Guide</a>



## Architecture
![image](https://github.com/user-attachments/assets/5aef55e9-bb00-4be4-90bd-71726153a66f)

![image](https://github.com/user-attachments/assets/754cbc0e-942d-4dd3-a646-cf1022a6c686)

*Ref 1: Network Diagram*


### Setup Details
-	Wazuh was deployed on a cloud server to monitor activity from endpoint devices.
-	Shuffle was installed on a separate cloud server for orchestration and automation.
-	The Hive was hosted on another cloud server for case management and collaboration.
-	The monitored endpoint: Windows machine (DESKTOP-8AAR6BV (002)).

## Workflow
1.	Threat Generation and Detection:
-	A Mimikatz alert was triggered on the Windows endpoint (DESKTOP-8AAR6BV (002)).
-	Wazuh detected the alert and generated detailed logs, including a SHA256 hash of the suspected malware.
![image](https://github.com/user-attachments/assets/06f8e34c-5492-4917-b23f-11663a3f04b6)

*Ref 2: Mimikatz File executed on Windows client Machine*

![image](https://github.com/user-attachments/assets/75b16c47-8d81-493b-9a84-44e82fc451a2)

*Ref 3a: Mimikatz alert detected on Wazuh*

![image](https://github.com/user-attachments/assets/c7ad6e4e-b4ed-4d92-85ec-dbfef825ffbe)

*Ref 3b: Mimikatz alert detected on Wazuh*

2.	Automation with Shuffle:
-	Wazuh sent the alert to Shuffle.
-	Shuffle extracted the SHA256 hash from the alert and queried VirusTotal for a reputation score.
-	Shuffle triggered additional actions based on the alert severity:
    o	Sending the alert to The Hive for case management.
    o	Sending an email notification to the SOC analyst.
 	
![image](https://github.com/user-attachments/assets/8f7708ed-0706-4bb3-911c-35740f361901)

*Ref 4: Shuffle Workflow*

![image](https://github.com/user-attachments/assets/21bc30ca-0ab9-4938-946c-1b86e721edcb)

*Ref 5: Data ingested to shuffle from Wazuh*

![image](https://github.com/user-attachments/assets/1bfa73eb-80ef-4d24-92d6-02422cd56037)

*Ref 6: SHA Regex to extract Hash value*

![image](https://github.com/user-attachments/assets/b305b7e7-d365-431c-94da-29aefedcc146)

*Ref 7: Virustotal results*

![image](https://github.com/user-attachments/assets/7f5f7ac9-141b-4099-a67d-c072f58bf0b1)

*Ref 8: Shuffle sending Alerts to The Hive and Email*

3.	Incident Management in The Hive:
-	The Hive received the alert as a new case with detailed information.
-	The SOC team could review, escalate, or close the case after investigation.

![image](https://github.com/user-attachments/assets/ec81a4df-8a99-4b1f-a550-4b0b926f46ee)

*Ref 9: Alert sent to The Hive*

![image](https://github.com/user-attachments/assets/d83922f1-f3b7-45f7-8b9b-03b455f80e6a)

*Ref 10: Alert sent to Email*

4.	Defensive Capabilities:
-	Shuffle workflows included automatic blocking of malicious IP addresses identified in the alerts.

## Conclusion
This SOC Automation Lab demonstrates the power of integrating open-source tools to build an efficient, automated incident response workflow. By combining monitoring, automation, and case management, the lab enhances the SOC's capability to detect, analyze, and respond to threats quickly and effectively.









