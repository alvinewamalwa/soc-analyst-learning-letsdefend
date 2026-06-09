# SIEM Investigation – Phishing Alert Case (Event ID 257)

This folder documents a SOC investigation performed on a phishing alert generated in the LetsDefend SIEM platform. The case involved analyzing a deceptive email, identifying malicious indicators, and reviewing endpoint activity to determine potential compromise.

## Alert Overview

The alert was triggered by rule SOC282 – Phishing Alert: Deceptive Mail Detected.

I began the investigation by reviewing the full alert details to understand the context, including sender information, SMTP IP address, recipient, and email classification as shown below.

![Description](/SIEM-investigation/screenshots/detailed-info-257.png)



## Email Investigation

I analyzed the email directly from the Email Security interface on Letsdefend platform by entering the sender's email address. It was sent to Felix and contained a phishing lure designed to appear legitimate.

I reviewed the sender email, subject line, and content in detail. The message used social engineering techniques, including urgency and reward-based deception.

A call-to-action button labeled “Redeem Now” was visible within the email content, encouraging the user to interact with the message.

The email also contained a password-protected ZIP attachment named “free-coffee.zip”, with the password provided as “infected”.

 ![Description](/SIEM-investigation/screenshots/phishing-email-1.png)![Description](/SIEM-investigation/screenshots/phishing-email-2.png)![Description](/SIEM-investigation/screenshots/phishing-email-3.png)



## Investigation Summary

I analyzed the attachment using a sandbox environment known as Hybrid Analysis and confirmed to be malicious.

I used Threat Intel to validate indicators associated with the file and infrastructure.



My Playbook

After successfully investigating the alert and closing the case, I came up with my own playbook `https://app.letsdefend.io/case-management/casedetail/alvine12w/257` about the case.
Playbook Note
The alert (Event ID 257) was triggered by rule SOC282 indicating a potential phishing email. Analysis of the email metadata shows that it originated from SMTP IP 103.80.134.63 with sender address free@coffeeshooop.com, which appears suspicious and potentially spoofed. The subject "Free Coffee Voucher" suggests a social engineering attempt to lure the recipient. No URLs or attachments were identified in the email, and there is no evidence of user interaction or execution of malicious content on the host. Based on the analysis, the alert is classified as a phishing attempt with no confirmed compromise. Recommended actions include monitoring or blocking the sender address and performing further threat intelligence checks on the associated IP address.


## Remediation and Response Actions

Following the investigation of the phishing alert (Event ID 257), the following remediation and response actions are recommended based on the findings.

### 1. Email Containment

* The malicious email should be removed from the affected user’s mailbox.
* The sender address and associated domain should be blocked at the email gateway to prevent further delivery attempts.
* Similar emails should be searched across the organization to identify potential exposure to other users.

### 2. Sender and Infrastructure Blocking

* Block the sender email address `free@coffeeshooop.com`.
* Block or monitor the associated SMTP IP address `103.80.134.63` in security controls.
* Add indicators of compromise (IOCs) to threat intelligence and email filtering systems.

### 3. Endpoint Protection

* Ensure endpoint security tools are active and updated.
* Scan the affected host for any residual malicious files or artifacts.
* Confirm that no malicious processes or persistence mechanisms exist on the system.

### 4. Threat Intelligence Actions

* Enrich the SMTP IP address and sender domain using threat intelligence platforms.
* Update internal detection rules based on observed phishing patterns and indicators.

### 5. User Awareness

* Inform the affected user about the phishing attempt.
* Conduct phishing awareness training focusing on social engineering techniques such as urgency and reward-based scams.

### 6. Monitoring and Detection Improvement

* Increase monitoring for similar phishing patterns, especially emails using reward-based lures.
* Update SIEM rules to detect similar attachments, domains, and behavioral indicators.
* Review logs for any related activity from the same IP or domain across the environment.

### Conclusion

These remediation steps ensure containment of the identified phishing attempt, reduce the risk of recurrence, and strengthen overall detection and response capabilities within the environment.

