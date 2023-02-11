
# 1. Scope

The scope ofthis assessment was one internal network range and the INLANEFREIGHT.LOCAL Active Directory domain.

![[Pasted image 20230211163823.png]]

Assessment Overview and Recommendations

During the internal penetration test against Inlanefreight, Hack The Box Academy identified seven (7) findings that threaten the confidentiality, integrity, and availability of Inlanefreight’s information systems. The findings were categorized by severity level, with five (5) of the findings being assigned a high-risk rating, one (1) medium-risk, and one (1) low risk. There was also one (1) informational finding related to enhancing security monitoring capabilities within the internal network. The tester found Inlanefreight’s patch and vulnerability management to be well-maintained. None of the findings in this report were related to missing operating system or third-party patches of known vulnerabilities in services and applications that could result in unauthorized access and system compromise. Each flaw discovered during testing was related to a misconfiguration or lack of hardening, with most falling under the categories of weak authentication and weak authorization. One finding involved a network communication protocol that can be “spoofed” to retrieve passwords for internal users that can be used to gain unauthorized access if an attacker can gain unauthorized access to the network without credentials. In most corporate environments, this protocol is unnecessary and can be disabled. It is enabled by default primarily for small and medium sized businesses that do not have the resources for a dedicated hostname resolution (the “phonebook” of your network) server. During the assessment, the presence of these resources was observed on the network, so Inlanefreight should begin formulating a test plan to disable the dangerous service.

# 2. Network Penetration Test Assessment Summary

Inlanefreight provided the tester with network ranges but did not provide additional information such as operating system or configuration information.

Summary of Findings 

During the course of testing, Hack The Box Academy uncovered a total of seven (7) findings that pose a material risk to Inlanefreight’s information systems. Hack The Box Academy also identified one informational finding that, if addressed, could further strengthen Inlanefreight’s overall security posture. Informational findings are observations for areas of improvement by the organization and do not represent security vulnerabilities on their own. The below table provides a summary of the findings by severity level.

![[Pasted image 20230211164206.png]]

# 3. Internal Network Compromise Walkthrough

During the course of the assessment Hack The Box Academy was able gain a foothold and compromise the internal network, leading to full administrative control over the INLANEFREIGHT.LOCAL Active Directory domain. The steps below demonstrate the steps taken from initial access to compromise and does not include all vulnerabilities and misconfigurations discovered during the course of testing.

Detailed Walkthrough

![[Pasted image 20230211164510.png]]

Detailed reproduction steps for this attack chain are as follows:

Upon connecting to the network, the tester started the Responder tool and was able to capture a password hash for the bsmith user by spoofing NBT-NS/LLMNR traffic on the local network segment.

![[Pasted image 20230211164543.png]]

# 4. Remediation Summary

![[Pasted image 20230211164609.png]]

# 5. Technical Findings Details

1. LLMNR/NBT-NS Response Spoofing - High

![[Pasted image 20230211164707.png]]

Finding Evidence:

![[Pasted image 20230211164736.png]]

# 6. Appendices

![[Pasted image 20230211164827.png]]


![[Pasted image 20230211164841.png]]

![[Pasted image 20230211164850.png]]

![[Pasted image 20230211164900.png]]

![[Pasted image 20230211164908.png]]

![[Pasted image 20230211164912.png]]

