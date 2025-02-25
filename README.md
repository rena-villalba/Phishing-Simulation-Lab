## Phishing Simulation Lab with Automated Incident Response

## Overview

This project is a phishing simulation lab that demonstrates how a malicious email can be crafted and detected using security automation tools. The lab involves a Windows Virtual Machine (VM) acting as the target, where an attacker sends a phishing email impersonating Microsoft Support to trick the user into clicking a fake update link. However, instead of leading to a malicious payload, the hyperlink in this simulation redirects to nmap.org as a proof-of-concept.

The lab also incorporates real-time monitoring, detection, and response mechanisms using LimaCharlie, Tines, and VirusTotal to analyze the phishing attempt and provide automated mitigation options.

## Key Components & Workflow
- 1. Phishing Email Creation & Delivery

  A spoofed email is crafted using Emkei’s Fake Mailer, impersonating Microsoft Support.The email contains a hyperlink disguised as an Outlook update. A temporary mailbox is created using Square X to receive the spoofed email.

- 2. Target System & Monitoring

  The phishing email is sent to the Windows VM, acting as the simulated victim machine. LimaCharlie is configured as a real-time sensor on the VM to monitor for suspicious activity.

- 3. Detection & Automated Response

  If the link is clicked (either directly in the email or via an attachment), LimaCharlie generates an alert. The alert is forwarded to Tines, which triggers an automated incident response workflow. Tines uses the VirusTotal API to analyze the URL and retrieve its reputation data.

- 4. User Notification & Isolation Decision

  Tines sends an email alert to the temporary mailbox with details of the URL analysis. A user prompt is generated in Tines, asking whether the compromised machine should be isolated. If the user selects "Yes", Tines communicates with LimaCharlie to isolate the VM from the network for further investigation. A final email notification is sent, confirming the machine’s isolation status. If the user selects "No", an email is sent stating that the sensor remains active but unisolated.

## Technologies Used
- Windows VM (Target system)
- Emkei’s Fake Mailer (Email spoofing)
- Square X (Temporary mailbox)
- LimaCharlie (Security monitoring & detection)
- Tines (Automation & orchestration)
- VirusTotal API (URL reputation analysis)

## Use Cases
- Security awareness training: Simulating phishing attacks for cybersecurity education.
- Incident response automation: Demonstrating how automated security workflows can detect and mitigate phishing threats.
- Threat detection testing: Evaluating LimaCharlie’s monitoring capabilities in detecting phishing incidents.

## Limitations & Future Improvements
  This lab presents a basic phishing simulation, using a simple spoofed email and a benign hyperlink for demonstration purposes. However, in real-world scenarios, phishing attacks can be more sophisticated, involving weaponized attachments, credential harvesting pages, or more advanced evasion techniques.

  While this project is a foundational exercise, its primary goal is to showcase how automated security responses can be used to detect and mitigate phishing threats. The lab can be improved by:

  - Enhancing email realism: Using more convincing phishing tactics, such as dynamic sender spoofing or cloned login pages.
  - Expanding detection capabilities: Integrating sandboxing for attachments or AI-driven anomaly detection.
  - Improving response actions: Automating forensic data collection, logging incidents in SIEM platforms, or integrating with security orchestration tools.

## Lab Screenshots

*Img 1, Img 2: Spoofed Email*<br>
![Screenshot 2025-02-25 125930](https://github.com/user-attachments/assets/95a7106b-4e59-4a39-b7dd-bdcf9d59e952)
![Screenshot 2025-02-25 125946](https://github.com/user-attachments/assets/c20d6250-c318-485e-9cfd-005a13ea25ac)

*Img 3: Received fake Email*<br>
![1 fake_email](https://github.com/user-attachments/assets/1c3ef7d9-053c-4b99-b026-f8a5935344fb)

*Img 4: Current Status of the Sensor*<br>
![Screenshot 2025-02-25 023649](https://github.com/user-attachments/assets/27921bb8-ef26-4cdf-8c8b-673816aafb19)

*Img5: Searched Event on LimaCharlie*<br>
<img width="817" alt="2 timeline_section" src="https://github.com/user-attachments/assets/41a0a8f6-1996-4fee-883a-89230e1047b4" />

*Img6, Img7: Alert and Response created*<br>
<img width="169" alt="3 detection_alert" src="https://github.com/user-attachments/assets/ddfabc3f-6f60-4f03-97cb-9e58d1090a5d" />
<img width="306" alt="4 detection_response" src="https://github.com/user-attachments/assets/5c4dcadb-5545-4e16-a6e0-a4834581faf4" />

*Img 8: Detection Caught*<br>
![5 detection_caugth](https://github.com/user-attachments/assets/ec054d9e-64ad-46b3-b72a-8e8e5fe33a4b)

*Img 9: Workflow Generated*<br>
<img width="443" alt="6 tines_workflow" src="https://github.com/user-attachments/assets/bb2d263a-fffb-4215-8bb9-3b5c1c027651" />

*Img 10: Email with VirusTotal simplified report*<br>
![Screenshot 2025-02-25 023517](https://github.com/user-attachments/assets/23881fa2-2e74-4d6e-8c94-f4f6ebcdb831)

*Img 11: User Prompt*<br>
![Screenshot 2025-02-25 023559](https://github.com/user-attachments/assets/dbf1ccd9-78c8-4459-9ae0-588c46cb611e)

*Img 12: Case where the Sensor hasn't been Isolated*<br>
<img width="322" alt="isolation_denied" src="https://github.com/user-attachments/assets/01f2f70c-4f71-480e-b5c0-07ad6b8e41f6" />

*Img 13: Case where the Sensor has been isolated*<br>
<img width="334" alt="iso" src="https://github.com/user-attachments/assets/60c5e8a8-f91e-4cc1-81eb-4d64581bbee3" />

*Img 14: Sensor Isolated*<br>
<img width="251" alt="isolation" src="https://github.com/user-attachments/assets/26a54e58-fc73-4659-b203-5ff9a1eab3fa" />

*Img 15: Testing connection*<br>
<img width="265" alt="isolation_test" src="https://github.com/user-attachments/assets/23cbbccd-2b47-4043-983c-99ac4d7f7866" />

