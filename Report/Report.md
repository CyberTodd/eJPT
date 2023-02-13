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
	- The general findings will provide a synopsis of the issues found during the penetration test in a basic and statistical format. Graphic representations of the targets tested, testing results, processes, attack scenarios, success rates, and other trendable metrics as defined within the pre engagement meeting should be present. In addition, the cause of the issues should be presented in an easy to read format. (ex. A graph showing the root cause of issues exploited)

![[Pasted image 20230213135054.png]]

> If defined within the Pre engagement exercise, this area should also include metrics which depict the effectiveness of the countermeasures within the environment. (ex.. we ran x attacks and IPS blocked y. Other countermeasures should also have similar metrics of design vs. effectiveness.)

5. Recommendation Summary
	- The recommendation section of the report should provide the reader with a high level understanding of the tasks needed to resolve the risks identified and the general level of effort required to implement the resolution path suggested. This section will also identify the weighting mechanisms used to prioritize the order of the road map following.

6. Strategic Roadmap
	- Roadmaps should include a prioritized plan for remediation of the insecure items found and should be weighed against the business objectives/ level of potential impact. This section should map directly to the goals identified as well as the threat matrix created in the PTES-Threat modeling section. By breaking up into predefined time/objective based goals, this section will create a path of action to follow in various increments. Example:

![[Pasted image 20230213135320.png]]
![[Pasted image 20230213135333.png]]
![[Pasted image 20230213135344.png]]

---
# 2. Technical Report

This section will communicate to the reader the technical details of the test and all of the aspects/components agreed upon as key success indicators within the pre engagement exercise. The technical report section will describe in detail the scope, information, attack path, impact and remediation suggestions of the test.

1. Introduction
	- The introduction section of the technical report is intended to be an initial inventory of:
		-   Personnel involved in the testing from both the Client and Penetration Testing Team
		-   Contact information
		-   Assets involved in testing
		-   Objectives of Test
		-   Scope of Test
		-   Strength of Test
		-   Approach
		-   Threat/Grading Structure

2. Information Gathering
	-  In this section, a number of items should be written up to show the CLIENT the extent of public and private information available through the execution of the Intelligence gathering phase of PTES. At a minimum, the results identified should be presented in 4 basic categories:
		1. Passive Intelligence
			- Intelligence gathered from indirect analysis such as DNS,Google dorking for IP/infrastructure related information. This section will focus on the techniques used to profile the technology in the CLIENT environment WITHOUT sending any traffic directly to the assets.
		2. Active Intelligence
			- This section will show the methods and results of tasks such as infrastructure mapping, port scanning, and architecture assessment and other foot printing activities. This section will focus on the techniques used to profile the technology in the CLIENT environment by sending traffic DIRECTLY to the assets.
		3. Corporate Intelligence
			- Information about the structure of the organization, business units, market share, vertical, and other corporate functions should be mapped to both business process and the previously identified physical assets being tested.
		4. Personnel Intelligence
			- 
1. Vulnerability Assessment
2. Exploitation/ Vulnerability Confirmation
3. Post Exploitation
4. Risk/Exposure
5. Conclusion