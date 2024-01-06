Phishing Analysis Report - 04/17/2023


Section 1: Email Description and Artifacts Collected
=======================================
Sender Address:
secured_file59848@nhfc.com

Subject Line:
Office Document

Recipient(s):
embryology@nhfc.com

Sender IP Address:
183.90.231.122

Reverse DNS:
xb728347@sv341.xbiz.ne.jp

Full URL (sanitized):
hxxps[://]priorityhealthconsultants[.]com/www/#embryology@nhfc[.]com

Main Domain:
hxxps[://]priorityhealthconsultants[.]com

Email Description:

The threat actor is using the spoofing tactic to spoof our domain @nhfc.com and sent a generic phishing email or could be a spear phishing because was targetting only our embryology email with no greetings. The email use HTML styling to make it looks legit but it shows a filename generated with HTML (not an actual attachment) with an button to a malicious website.



Section 2: Artifact Analysis
=======================================

WHOIS analysis - Performed reverse DNS of 183.90.231.122 shows the domain is from Japan

VirusTotal and WannaBroswer Analysis - Search the full URL on VT shows some security vendors flagged as malicious/phishing with the HTLM status code 403. Confirmed with searchin on WannaBroswer shows HTML code of 403 forbidden.

urlscan.io Analysis - Used URLSCAN to check the link destination shows 403 forbidden page. The main domain is hxxps[://]priorityhealthconsultants[.]com

Figured out the reason how the threat actor was able to spoof our domain with the help of Google Tech. The SPF key was double pasted on our DNS which prevented SPF to scan the incoming email correctly.



Section 3: Suggested Defensive Measures
=======================================

We blocked the full URL on our firewall as well as the sender IP address so in case a user accidentaly clicked the button, the communication between will be blocked. We also blocked the sender email address from the email gateway since the email is using @nhfc.com so blocking the entire domain might block all legit communication in our domain. No more email from the same sender address will be received in users' inboxes.

In addition, during analysis we found out the SPF configuration was wrongly pasted on our DNS (AWS). We fixed it and the applied changes might take 48 hours to be effective.
