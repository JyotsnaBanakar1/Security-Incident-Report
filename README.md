# Security-Incident-Report

Incident Report: Brute Force Attack and Website Compromise
Overview
This repository contains the detailed incident response report for the brute force attack that compromised the yummyrecipesforme.com website. A former employee executed the attack, exploiting weak security practices to gain administrative access. The attacker embedded malicious JavaScript into the website’s source code, redirecting users to a fake website and delivering malware. This README provides an analysis of the attack, the network protocols involved, and recommended security actions to prevent future brute force attacks.

Incident Summary
Attack Type: Brute Force Attack
The disgruntled former employee used a brute force technique to repeatedly guess the default administrative password until they successfully logged into the website’s admin panel.
After obtaining access, the attacker:
Embedded a malicious JavaScript function in the website’s source code.
Changed the admin account password, preventing the website owner from regaining access.
Modified the website to prompt users to download and run a malware-laden file.
Redirected visitors from yummyrecipesforme.com to a fake website (greatrecipesforme.com) containing the malware.
Customer Complaints
Several hours after the attack, customers reported that they were prompted to download a suspicious file from the website. Their systems slowed down after executing the file, and they noticed they were redirected to a different URL after running it.

Attack Investigation
To investigate, a sandbox environment was created, and the malicious website behavior was observed. By using tcpdump to capture network traffic, the following process was recorded:

DNS Request: The browser requested the IP address for yummyrecipesforme.com.
DNS Response: The DNS server returned the correct IP address.
HTTP Request: The browser requested the webpage from yummyrecipesforme.com using the provided IP address.
Malware Download: The website prompted a file download that contained the malware.
DNS Request: The browser requested the IP address for the fake website greatrecipesforme.com.
DNS Response: The DNS server returned the IP address for greatrecipesforme.com.
HTTP Request: The browser connected to greatrecipesforme.com, where the malware was hosted.
Network Protocols Used
DNS (Domain Name System): Translated the URLs of both yummyrecipesforme.com and greatrecipesforme.com into their respective IP addresses.
HTTP (Hypertext Transfer Protocol): Facilitated the requests and responses between the browser and the web servers for both the legitimate and malicious websites.
Analysis and Findings
Weak Password Security: The admin password was set to the default, allowing the attacker to easily guess it using brute force.
No Brute Force Prevention: There were no controls or protections in place to detect or block repeated login attempts.
Malicious Code Injection: The attacker embedded JavaScript into the website’s source code, initiating the malware download and redirection to the malicious website.
Redirection to Malicious Site: Once the user downloaded and ran the malware, their browser was redirected to greatrecipesforme.com, where further malicious activities could take place.
Recommended Security Actions
To prevent future brute force attacks and protect the website from similar incidents, the following security actions are recommended:

Enforce Strong Password Policies:

Require strong passwords for administrative accounts (minimum of 12 characters, mix of upper/lowercase letters, numbers, and special characters).
Disable default passwords upon setup.
Implement Brute Force Attack Prevention:

Use rate-limiting to restrict the number of login attempts from the same IP address.
Implement CAPTCHA after several failed login attempts to prevent automated brute force tools.
Enable account lockout after a specific number of failed login attempts.
Two-Factor Authentication (2FA):

Require 2FA for all administrative accounts, adding an extra layer of security to prevent unauthorized access.
Regular Security Audits:

Regularly audit website security settings and source code to detect any vulnerabilities or suspicious changes.
Web Application Firewall (WAF):

Deploy a WAF to filter and monitor HTTP requests, blocking common attack patterns such as brute force and code injection attempts.
Malware Scanning and Removal:

Implement regular malware scanning to detect and remove malicious files before they affect users.
Conclusion
The yummyrecipesforme.com website was compromised due to poor password management and lack of protections against brute force attacks. The attacker gained access to the admin panel, inserted malicious JavaScript code, and redirected users to a fake website that delivered malware. The recommended security actions, such as enforcing strong password policies, implementing brute force protections, and adding two-factor authentication, will help prevent future incidents and secure the website from further attacks.
