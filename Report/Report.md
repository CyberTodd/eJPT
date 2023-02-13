# 1. Executive Summary

1. Background 
	- This section should explain to the reader the overall purpose of the test. 
	- Details on the terms identified within the Pre Engagement section relating to risk, countermeasures, and testing goals.
	- -   If objectives were changed during the course of the testing then all changes must be listed in this section of the report. Additionally, the letter of amendment should be included in the appendix of the report and linked to from this section.

> Example
> (CLIENT) tasked (Pentester) with performing an internal/external vulnerability assessment and penetration testing of specific systems located in (logical area or physical location). These systems have been identified as (risk ranking) and contain (data classification level) data which, if accessed inappropriately, could cause material harm to (Client). In an effort to test (CLIENT’s) ability to defend against direct and indirect attack, (Pentester) executed a comprehensive network vulnerability scan, Vulnerability conformation( <-insert attack types agreed upon->) exploitation of weakened services, client side attacks, browser side attacks (etc) The purpose of this assessment was to verify the effectiveness of the security controls put in place by (CLIENT) to secure business-critical information. This report represents the findings from the assessment and the associated remediation recommendations to help CLIENT strengthen its security posture.


2. Overall Posture
	- This area will be a narrative of the overall effectiveness of the test and the pentesters ability to achieve the goals set forth within the pre engagement sessions. A brief description of the Systemic (ex. Systemic issue= Lacking Effective Patch Management Process vs. Symptomatic= Found MS08-067 missing on xyz box) issues identified through the testing process as well as the ability to achieve access to the goal information and identify a potential impact to the business.

3. Risk Ranking/ Profile
	- The overall risk ranking/profile/score will be identified and explained in this area. In the pre engagement section the Pentester will identify the scoring mechanism and the individual mechanism for tracking/grading risk. Various methods from FAIR, DREAD, and other custom rankings will be consolidated into environmental scores and defined.

![[Pasted image 20230213134814.png]]

> The “Overall Risk Score” for the (CLIENT) is currently a Seven (7). This rating implies an ELEVATED risk of security controls being compromised with the potential for material financial losses. The consultant determined this risk score based on one high risk and several medium risk vulnerabilities, along with the success of directed attack. The most severe vulnerability identified was the presence of default passwords in the corporate public facing website which allowed access to a number of sensitive documents and the ability to control content on the device. This vulnerability could lead to theft of user accounts, leakage of sensitive information, or full system compromise. Several lesser severe vulnerabilities could lead to theft of valid account credentials and leakage of information.

4. General Findings:
	- 

# 2. Technical Report