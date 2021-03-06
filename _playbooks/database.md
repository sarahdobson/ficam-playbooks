---
layout: playbook
title: Physical Access Control System Guide
description: This playbook helps you understand FICAM-compliant PACSs.
permalink: /playbooks/pacs/
toc: true
---
# Physical Access Control System Playbook

This _Physical Access Control System (PACS) Guide_ will help you understand concepts related to _Federal Identity, Credential, and Access Management_-compliant PACSs.  At a high level, a PACS is a collection of technologies that control physical access at one or more federal agency sites by electronically authenticating employees, contractors, and visitors. 

{% include alert-info.html content="The contents of this guide are meant to be informative and do not serve as the basis for determining PACS compliance. Agency-specific guidance should supersede the recommendations within this guide, where appropriate." %}

To learn more:
1. [What is a Physical Access Control System?]({{site.baseurl}}/what-is-pacs/)
1. [Physical Access Control System Deployment Models]({{site.baseurl}}/pacs/)
1. [Aligning Facility Security Level and Authentication]({{site.baseurl}}/alignfslandauth/)
1. [Procurements]({{site.baseurl}}/procure/)
1. [Training]({{site.baseurl}}/train/)
1. [Lessons Learned]({{site.baseurl}}/lessonslearned/)
1. [Standards, Policies, and Guidance]({{site.baseurl}}/standards/)
1. [Glossary]({{site.baseurl}}/glossary/)

## Questions and Contributions
This guide is open source and a _work in progress_, and we [welcome contributions]({{site.baseurl}}/contribute/) from our colleagues. Some topics may still be under development. If you have questions, please review the [GitHub Issues]({{ site.repo_url }}/issues) for in-progress information. If you would like to contribute or add a question, create a new [Issue]({{ site.repo_url }}/issues) or add a comment to an existing one. 

## Acknowledgment
We want to thank the Secure Technology Alliance, especially the members of the Access Control Council, for contributions to the *PACS Playbook* and permission to reuse content from their presentations and the *How to Plan, Procure and Deploy a PIV-Enabled Physical Access Control System* webinar training.  

# What is a PACS?

A Physical Access Control System (PACS) grants access to employees and contractors who work at or visit a site by electronically authenticating their PIV credentials. Although PACSs are Information Technology systems, they must be designed, deployed, and operated in cooperation with Physical Security teams to successfully meet agency mission needs. 


The following table defines common PACS components: 

| **Component** | **Description** |
|----------------|----------|
| **Access point** | Entrance point or physical barrier where an employee or contractor interacts with the PACS. Example access points include turnstiles, gates, and locking doors. |
| **PIV credential** | Federal employees and contractors use [Personal Identity Verification (PIV) credentials](https://piv.idmanagement.gov/elements/){:target="_blank"} to *physically access* federal facilities and *logically access* federal information systems. |
| **Credential reader and keypad** | The reader provides power to and reads data from a PIV credential. The reader also sends this data to a control panel to authenticate the PIV credential and request access authorization. Employees and contractors may need to enter a PIN into the keypad and add a biometric, depending on the facility's security classification and risk levels. | 
| **Biometric reader** | Captures biometric data (for example, fingerprint or iris scan) and verifies it against the PIV credential's biometric data. |
| **Control panel** | Receives the credential data sent by the reader and verifies its presence in the credential holder data repository. It then makes an access decision and transmits authorization data to the access control server and access point.  |
| **Access control server** | Grants authorization to the employee or contractor requesting access (for example, presenting a PIV credential to a reader). It also registers and enrolls employees and contractors; enrolls and validates credentials; and logs system events. |
| **Credential<br>holder data repository** | Contains employee and contractor data and physical access privileges. Control panels use this authoritative data to validate credential data. |
| **Auxiliary Systems** | Agencies may integrate the PACS with additional facility monitoring systems such as surveillance systems, fire alarm systems, and evacuation systems. |


{% include alert-info.html content="All agency-purchased PACS components must be FIPS 201-compliant and selected from <a href=\"https://www.idmanagement.gov/approved-products-list-pacs-products/\" target=\"_blank\">GSA's Approved Products List (APL) for PACS Products</a>. The products in this list have undergone vulnerability and interoperability testing through the FIPS 201 Evaluation Program. As an IT system, a PACS must still complete Certification and Accreditation and obtain an Authority to Operate from your agency before connecting to the network." %}


## Characteristics of a FICAM-Compliant PACS
In May 2019, the Office of Management and Budget (OMB) released memorandum [M-19-17](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}, _Enabling Mission Delivery through Improved Identity, Credential, and Access
Management_. Related to PACS, M-19-17 rescinded memorandum [M-11-11](https://obamawhitehouse.archives.gov/sites/default/files/omb/memoranda/2011/m11-11.pdf){:target="_blank"}, _Continued Implementation of Homeland Security Presidential Directive (HSPD) 12 – Policy for a Common Identification Standard for Federal Employees and Contractors_. The updated guidance adds further specificity to require the use of PIV credentials for physical access to Federal facilities, implemented per _[The Risk Management Process for Federal Facilities: An Interagency Security Committee Standard](https://www.dhs.gov/isc-policies-standards-best-practices){:target="_blank"}_ and NIST [SP 800-116, Revision 1](https://csrc.nist.gov/publications/detail/sp/800-116/rev-1/final){:target="_blank"}, _A Recommendation for the Use of PIV Credentials in Physical Access Control Systems (PACS)_.

Characteristics of NIST SP 800-116, Revision 1, compliant systems include, but are not limited to:
- Use high-assurance credentials for electronic authentication of employees and contractors.
- Use non-deprecated authentication mechanisms, as defined by [FIPS 201-2](https://csrc.nist.gov/publications/detail/fips/201/2/final){:target="_blank"}.
- Validate the status and authenticity of credentials.
- Interoperate with PIV credentials issued by other agencies.
- Use components listed on the GSA FIPS 201 Approved Products List (APL).


The next section, *[PACS Deployment Models]({{site.baseurl}}/pacs/)*, describes common deployment models for PACS.

# PACS Deployment Models

This page will give you a basic understanding of Physical Access Control System (PACS) deployment models. 

- [What Is a Standalone Physical Access Control System?](#what-is-a-standalone-pacs)
- [What Is an Enterprise Physical Access Control System?](#what-is-an-enterprise-pacs)

## What Is a Standalone PACS?

A standalone PACS is a local system that controls physical access to a facility or specific areas within it, for example, a Sensitive Compartmented Information Facility (SCIF). Standalone PACSs are facility-centric, and consequently, these systems typically do not connect to enterprise networks. While this deployment model tends to be the most common and uncomplicated method of managing access to controlled areas, it has several challenges.

### Standalone PACS' Operational Challenges

Agencies that use standalone PACSs have encountered operational challenges: 
* Sites must independently control physical access.
* Agencies see delays with credential transfers or terminations.
* Employees and contractors must re-enroll their credentials for all federal work sites that they visit.
* Departments inconsistently apply enterprise-wide security policies.
* Agencies experience reduced situational awareness (for example, logs cannot be correlated across the enterprise)
* Agencies with many standalone PACSs see increased human error, such as data entry errors.

{% include alert-success.html content="Can agencies centrally control physical access for most, or all, of their sites?  Yes - the answer is to implement an Enterprise Physical Access Control System." %}

## What Is an Enterprise PACS?

An Enterprise PACS (E-PACS) extends the concept of a standalone PACS to act as a unified, enterprise-wide system that controls physical access at most (or all) sites that belong to an agency. E-PACSs address the operational challenges of standalone PACSs and improve system management, scalability, monitoring, and performance. 

E-PACSs rely on the same components as standalone PACSs. However, an essential architectural distinction is that an E-PACS connects to an agency's enterprise-network, whereas a PACS typically does not.

{% include alert-info.html content="Some agencies need standalone PACSs for their unique sites and missions, but most agencies could benefit from transitioning to an E-PACS." %}

### Would an Enterprise PACS Work for Our Agency?

Here are some key E-PACS advantages to consider:

* One enterprise-wide system controls physical access for many (or all) agency sites.
* One employee and contractor enrollment system that connects multiple enrollment locations.
* One credential registration and provisioning point.
* One enterprise-wide system for administrators to modify or terminate access privileges.
* One enterprise-wide system that regularly polls for [Certificate Revocation List](https://piv.idmanagement.gov/pivcertchains/#revocation){:target="_blank"} (CRL) updates and maintains revocation data.
* Reduced costs for system management, such as patching, server system administration, and software updates.
* Reduced costs for reporting , such as Federal Information Security Modernization Act [FISMA] reporting.
* Reduced costs for:
    * Server hardware
    * System security assessment and accreditation

	
The next section, *[Aligning Facility Security Level (FSL) and Authentication]({{site.baseurl}}/alignfslandauth/)*, explains the processes needed to prepare for a PACS deployment and offers more detail related to the FIPS 201-approved PIV authentication mechanisms.

# Aligning Facility Security Level (FSL) and Authentication

Federal agencies rely on Physical Access Control Systems (PACSs) and Personal Identity Verification (PIV) credentials to confirm that an employee, contractor, or visitor _is_ or _is not_ authorized to access a site and its critical assets, such as systems, information, and people. 

To protect your agency's critical assets, you must assess each site's risk level (called *Facility Security Level*) and decide what level of PIV credential authentication is required (called *authentication mechanism*). 

The FSL and Authentication checklist below will help you:

- [Assess Facility Security Level](#assess-facility-security-level)
- [Categorize security areas](#categorize-security-areas)
- [Determine authentication factors](#determine-authentication-factors)
- [Select the authentication mechanisms needed to protect critical assets](#select-authentication-mechanisms)

## Assess Facility Security Level

{% include alert-info.html content="These federal standards give guidance for assessing FSL, including how to categorize site risks:<br> - <a href=\"https://www.dhs.gov/publication/isc-risk-management-process\" target=\"_blank\">The Risk Management Process for Federal Facilities: An Interagency Security Committee Standard </a> <br> - <a href=\"https://csrc.nist.gov/publications/detail/sp/800-116/rev-1/final\" target=\"_blank\">NIST SP 800-116, Revision 1, Guidelines for the Use of PIV Credentials in Facility Access. </a>" %}

<i class="fa fa-check-square-o"></i> &nbsp;**Inventory critical assets for each agency site**
- When you inventory critical assets, also document any challenges to secure them.  <br><br>Examples of critical assets include:
    - People
    - Information systems and IT infrastructure
    - Campuses, buildings, secure vaults, and armories
    - Tenant agencies' people, information systems, and IT infrastructure
  
- If you must evaluate an asset's criticality, consider:
    - Security classification level
    - Impact on national security from potential asset loss, compromise, or damage
    - Cost of replacing the asset

<i class="fa fa-check-square-o"></i> &nbsp;**Assess site and critical asset risks, as well as risks to tenant agencies' assets**
- Examples of potential risks to a site and its critical assets include: 
    - Site mission(s) (those of the agency, its organizations, and tenant agencies)
    - Site “symbolism” (public perception of the agency, its organizations, tenant agencies, or missions)
    - Total population (employees plus contractors)
    - Size (square footage) 
    - Geographical location
    - Proximity to other facilities or structures not owned by the agency
    - Threats specific to tenant agencies 
        
 - Consider the following for each asset: 
    - Criticality - Is it mission-critical?
    - Sensitivity - Does it contain classified or sensitive information?
    - Likelihood - What is the probability of loss, compromise, or damage?

<i class="fa fa-check-square-o"></i> &nbsp;**Categorize each asset by risk impact level**
- [FIPS 199](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.199.pdf){:target="_blank"} defines three (3) impact levels on organizations and people (that is, a loss of confidentiality, integrity, or availability): 
   
|Impact Level | Description |
|:---------|:------------|
| *Low*| The loss of confidentiality, integrity, or availability could have a **limited** adverse effect on organizational operations, organizational assets, or individuals.|
| *Moderate* | The loss of confidentiality, integrity, or availability could have a **serious** adverse effect on organizational operations, organizational assets, or individuals.| 
|*High* | The loss of confidentiality, integrity, or availability could have a **severe or catastrophic** adverse effect on organizational operations, organizational assets, or individuals. |

<i class="fa fa-check-square-o"></i> &nbsp;**Create a site map of categorized assets**
- This map will help you determine each security area's minimum security level.


{% include alert-info.html content="As an alternative to assessing a site's risk, you can select a pre-determined FSL as described in <a href=\"https://www.dhs.gov/publication/isc-risk-management-process/\" target=\"_blank\">The Risk Management Process for Federal Facilities: An Interagency Security Committee Standard</a>." %}



## Categorize Security Areas

{% include alert-info.html content="Agencies may use different terms for their security areas; however, each agency should establish its criteria for authentication mechanisms, according to <a href=\"https://csrc.nist.gov/publications/detail/sp/800-116/rev-1/final\" target=\"_blank\">NIST SP 800-116, Revision 1, Guidelines for the Use of PIV Credentials in Facility Access</a>." %}

<i class="fa fa-check-square-o"></i> &nbsp;**Categorize security areas** 
- Once you've inventoried and mapped assets by risk and impact level, it's time to categorize security areas.
- NIST SP 800-116, Revision 1, defines three (3) security area categories: 

|Category | Description|
|:---------|:------------|
| *Exclusion*| An area where uncontrolled movement would permit direct access to a security asset, such as a Sensitive Compartmented Information Facility (SCIF).|
| *Limited* | An area near a secure asset.  Uncontrolled movement within a limited area may permit access to an asset.  Escorts and other restrictions can prevent access.| 
|*Controlled* | An area near or surrounding a Limited or Exclusion area, such as a facility lobby. A Controlled area provides administrative control, safety, or a buffer zone for embedded Limited or Exclusion areas.  Movement of authorized personnel within this area usually is not controlled, as this area doesn't provide immediate access to secure assets.  |

- Assign the same risk level as the highest risk asset within the area. 
    - Example: If three (3) assets exist within a security area: one Low-risk, one Moderate-risk, and one High-risk, you must categorize the security area as **High-risk**.  Alternatively, the area may be split into three (3) security areas that each have a different risk level.  


## Determine Authentication Factors

{% include alert-info.html content="<a href=\"https://csrc.nist.gov/publications/detail/sp/800-116/rev-1/final\" target=\"_blank\">NIST SP 800-116, Revision 1, Guidelines for the Use of PIV Credentials in Facility Access</a> recommends the following method to determine authentication factors for Exclusion, Limited and Controlled security areas." %}

<i class="fa fa-check-square-o"></i> &nbsp;**Determine authentication factors required for security area categories** 

- Once you have categorized all security area categories, you will select the minimum number of authentication factors (1, 2, or 3) needed to access and safeguard the facility:

| Category| Minimum Number of Factors | Description|
|:---------|:--------------------------:|:------------|
|*Exclusion*| 3| Exclusion areas require all three authentication factors: Something you have, such as a PIV credential; something you know, such as the PIV credential PIN; and something you are, such as a fingerprint or iris scan.|
|*Limited* | 2 | Limited areas require 2 of the 3 authentication factors, such as a PIV credential and PIN or a PIV credential and fingerprint or iris scan.|
|*Controlled* | 1 | Controlled areas require only one authentication factor, such as a PIV credential.|  
  

## Select Authentication Mechanisms 

{% include alert-info.html content="<a href=\"https://csrc.nist.gov/publications/detail/fips/201/2/final\" target=\"_blank\">FIPS 201-2</a>, Personal Identity Verification (PIV) of Federal Employees and Contractors, defines authentication mechanisms at four assurance levels (Little or No, Some, High, and Very High)." %}

<i class="fa fa-check-square-o"></i> &nbsp;**Select authentication mechanism for each security area** 

- Based on the security area categories and required authentication factors for each security area, choose the PIV credential authentication mechanism(s) that enforce these factors at each access point. 
- FIPS 201-2 specifies these authentication mechanisms for PIV credentials:
    - PKI authentication using the PIV Authentication Certificate [(PKI-AUTH)]({{site.baseurl}}/glossary/#pki-auth){:target="_blank"} 
    - PKI authentication using the Card Authentication Certificate [(PKI-CAK)]({{site.baseurl}}/glossary/#pki-cak){:target="_blank"} 
    - Authentication using the Symmetric Card Authentication Key [(SYM-CAK)]({{site.baseurl}}/glossary/#sym-cak){:target="_blank"} 
    - Unattended authentication using off-card biometric comparisons [(BIO)]({{site.baseurl}}/glossary/#bio){:target="_blank"} 
    - Attended authentication using off-card biometric comparisons [(BIO-A)]({{site.baseurl}}/glossary/#bio-a){:target="_blank"} 
    - Either attended or unattended authentication using off-card biometric comparisons [(BIO(-A))]({{site.baseurl}}/glossary/#bio-a){:target="_blank"} 
    - Authentication using on-card biometric comparisons [(OCC-AUTH)]({{site.baseurl}}/glossary/#occ-auth){:target="_blank"} 


The table below gives the possible authentication mechanisms for the three (3) security area categories defined by NIST SP 800-116, Revision 1:

| Category  | Minimum<br>Number of<br>Factors | Acceptable Factors | Authentication<br>Mechanism:<br>Contact Interface  |  Authentication Mechanism:<br>Contactless Interface |
| :-------- | :------: | :----- | :-----  | :-----     |
| *Exclusion*  | 3 | Something you have **AND**<br>Something you know **AND**<br>Something you are | PKI-AUTH + BIO  | N/A |
| *Limited*   | 2 |Something you have *AND*<br>Something you know, **OR**<br>Something you have *AND*<br>Something you are, **OR**<br>Something you know *AND*<br>Something you are  | PKI-AUTH (with PIN or OCC) or<br>OCC-AUTH  |  OCC-AUTH |
| *Controlled*   | 1 | Something you have **OR**<br>Something you are  |  PKI-CAK  | PKI-CAK<br> SYM-CAK   |

**Note:** Some authentication mechanisms defined by NIST SP 800-116, Revision 1 might not be available on all user-population cards (for example, on-card biometric comparison or PKI-CAK). 

{% include alert-info.html content="When using PKI-CAK and PKI-AUTH as authentication mechanisms, certificates must be validated. Verify the certificate against a Certificate Revocation List (CRL) or Online Certificate Status Protocol (OCSP) server response. Also, verify that the certificate chains to the Federal Common Policy root certification authority (CA). Visit <a href=\"https://piv.idmanagement.gov/pivcertchains/\" target=\"_blank\">PIV Guides</a> to learn more about certificate trust." %}

<br>

The next section, *[Procurements]({{site.baseurl}}/procure/)*, describes the processes and resources needed for a PACS procurement.

# Procurements

{% include alert-info.html content="A good starting point that will help you understand Physical Access Control System procurements is GSA’s <a href=\"https://www.gsa.gov/cdnstatic/General_Supplies__Services/Guide_to_PACS_v2%2006-12-2018.pdf\" target=\"_blank\">PACS Customer Ordering Guide. </a>" %}

This page provides a sample PACS Procurement Checklist. You can reuse or tailor this checklist according to your agency’s practices. The checklist highlights common procurement activities as they relate to the following roles:
- Information Technology or Physical Security Engineers (ENG)
- Project Managers (PM)
- Procurement Officers (PO)
- Chief Information Officers (CIO)
- Chief Security Officers (CSO)

Agency staff are encouraged to participate in steps where their roles are listed in blue, bold font.

## PACS Procurement Checklist 

<style>
.title {font-size: 20px; color: white; background-color: #112e51; font-weight: 900;}
.header {text-align: center; font-size: 20px; color: white; background-color: #112e51; font-weight: 900;}

.what {  text-align: left; font-weight: 900; background-color: #f2f2f2; font size="5";}
.who { text-align: center; min-width: 55px; max-width: 55px; font-size: 12px; font-weight: 300; padding: 3px; background-color: #f2f2f2;}
#whoactive { font-weight: 800; color: #0071bc; }
</style>

<table>
 <col width="400">
 <col width="200">

 <tr>
  <th colspan="2" class="title">PACS Procurement Checklist</th>
  <th colspan="5" class="header">Recommended Participants</th>
 </tr>

 <tr>
  <td colspan="2" class="what">1. Identify agency’s need to procure or upgrade a PACS.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Determine whether your agency has a similar effort underway or other projects that could impact the procurement.</li>
	<li>Determine why the agency needs to procure or upgrade a PACS.</li>
	<li>Perform a cost-benefit analysis.</li>
  </ul>
  </td>
</tr>


 <tr>
  <td colspan="2" class="what">2. Develop a PACS project charter.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Identify the PACS project’s executive sponsor.</li>
	<li>Document a high-level project purpose, scope, and goals.</li>
	<li>Determine the PACS deployment model required for the project's scope.</li>
	<li>Identify what standards and requirements need to be addressed (for example, HSPD-12, FIPS 201-2, NIST SP 800-116, Revision 1).</li>
	<li>Estimate project duration.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">3. Identify and obtain support from PACS stakeholders (iterative).</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Identify your required and optional stakeholders and request their participation.</li>
	<li>Include national, regional, state, and local stakeholders.</li>
	<li>Involve stakeholders from agency Information Technology (IT) teams (for example, architect/engineers, network engineers, security, infrastructure services, directory services, web services).</li>
	<li>Involve agency facility and personnel support organizations (for example, physical security, building operations, Human Resources).</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">4. Identify PACS project phases and tasks (iterative).</td>
  <td class="who" id="whoactive">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Document the project’s phases and required tasks. Samples can include:
		<ul>
			<li>Pre-project planning</li>
			<li>Site security assessment(s)</li>
			<li>Develop Statement of Work (SOW)</li>
			<li>Develop PACS Requirements Document (or Specification)</li>
			<li>Develop and release Request for Information (RFI)</li>
			<li>Request for Proposal (RFP)/Request for Quotation (RFQ)</li>
			<li>Integrator (vendor) evaluation and award</li>
			<li>Design</li>
			<li>Implementation</li>
			<li>Inspections</li>
			<li>Testing</li>
			<li>Close-out</li>
			<li>Sustainment</li>
		</ul>
		</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">5. Develop a project schedule (iterative).</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Use automated tools or agency software to create a project schedule (that is, project tasks, dependencies, durations, and resources).</li>
	<li>Share the project schedule with stakeholders to ensure its accuracy and completeness.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">6. Conduct a Facility Security Level (FSL) assessment of project-related agency sites and determine Personal Identity Verification (PIV) authentication mechanisms for each site.</td>
  <td class="who" id="whoactive">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>For details, see <a href="{{site.baseurl}}/alignfslandauth/" target="_blank">Aligning FSL and Authentication Mechanism</a>.</li>
	<li>The FSL assessment and chosen PIV authentication mechanisms will form the basis for the PACS requirements document/specification, as well as affect the SOW and project costs.</li>
	<li>The sample survey questions below will help you assess the FSL of each facility and select the right PIV authentication mechanisms:
	<ul>
		<li>Who will use a facility’s PACS? Include all possible users.</li>
		<li>What credentials do the facility’s users and visitors have?</li>
		<li>What facility access risks exist?</li>
		<li>How can the facility mitigate these risks?</li>
		<li>What PACS installations does the facility need?</li>
		<li>What support systems would be integrated into the facility’s PACS (for example, intrusion detection, video surveillance, emergency notification, elevator control)?</li>
		<li>What PACS integrator or other contractor services does the agency need to solicit bids on?</li>
		<li>What PACS hardware and software is needed?</li>
	</ul>
	</li>
	<li>Your agency’s selected integrator will help select the approved, needed hardware and software through the GSA Acquisitions process (Schedules 70 and 84, Blanket Purchase Orders, etc.). The following are some useful considerations:
	<ul>
		<li>What are the facility’s common ingress and egress traffic patterns?</li>
		<li>What throughput speeds are needed?</li>
		<li>What are the ongoing operational and projected maintenance needs?</li>
		<li>What are the training needs for PACS administrators, operators, technicians, and users?</li>
		<li>Which PIV authentication mechanism(s) will be needed to secure the facility?</li>
	</ul>
	</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">7. Develop a PACS requirements document or specification.</td>
  <td class="who" id="whoactive">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>When documenting PACS requirements, it’s critical to solicit input from your stakeholders.</li>
	<li>Organize requirements into clear categories (for example, technical, performance, and operational) to help stakeholder’s give targeted feedback.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">8. Release a Request for Information (RFI) to potential service providers.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Create and issue an RFI to vendors that requests specific qualifications and capabilities against PACS requirements.</li>
  </ul>
  </td>
</tr>


 <tr>
  <td colspan="2" class="what">9. Submit an IT funding proposal following your agency’s budgetary process.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Follow your agency's existing budgetary procedures to submit a funding proposal for the project.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">10. Develop an RFP and SOW to solicit GSA-approved integrator bids.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>You can reuse the <a href="https://www.gsa.gov/cdnstatic/General_Supplies__Services/Guide_to_PACS_v2%2006-12-2018.pdf" target="_blank">GSA PACS Customer Ordering Guide’s Sample Statement of Work</a>, page 17. For help creating an RFP, see <a href="https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/Procurement-Language-1.1.0.pdf" target="_blank"> Enabling Strong Authentication with PIV Cards: PKI in PACS Recommended Procurement Language for RFPs</a>. For help with Requests for Quotations (RFQs), see <a href="https://www.ebuy.gsa.gov/ebuy/" target="_blank"> GSA’s eBuy RFQ Online Tool</a>.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">11. Solicit bids, evaluate, and award integrator contract.</td>
  <td class="who" id="whoactive">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Include these steps during your bid and evaluation process:
	<ul>
		<li>Identify members of the evaluation committee.</li>
		<li>Establish evaluation criteria for bid review.</li>
		<li>Identify how well proposed integrator solutions meet your needs.</li>
		<li>Document the award rationale and announce contract award decision.</li>
		<li>Upon request, provide a brief explanation of the award rationale to unsuccessful bidder(s).</li>
	</ul>
	</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">12. Develop a PACS architecture and migration strategy.</td>
  <td class="who" id="whoactive">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who">PO</td>
  <td class="who" id="whoactive">CIO</td>
  <td class="who" id="whoactive">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>Define a migration strategy to transition facilities to the new PACS solution.</li>
  </ul>
  </td>
</tr>

 <tr>
  <td colspan="2" class="what">13. Buy products listed on the GSA PACS APL.</td>
  <td class="who">ENG</td>
  <td class="who" id="whoactive">PM</td>
  <td class="who" id="whoactive">PO</td>
  <td class="who">CIO</td>
  <td class="who">CSO</td>
 </tr>

<tr>
  <td colspan="7" class="desc">
  <ul>
	<li>After contract award, your integrator will help you:
	<ul>
	<li>Choose the best PACS topology (that is, an end-to-end solution of hardware, software, a Certificate Validation System, and PIV credential readers) listed on the <a href="https://www.idmanagement.gov/approved-products-list-pacs-products/" target="_blank">GSA PACS APL</a> for the PIV authentication mechanisms selected for your facility.</li>
	<li>Buy the products and additional services you need by using the <a href="https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/schedules-news-and-updates" target="_blank">GSA MAS</a>, <a href="https://www.gsa.gov/technology/technology-purchasing-programs/it-schedule-70" target="_blank">GSA Schedule 70</a>, or <a href="https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/list-of-gsa-schedules/schedule-84security-fire-law-enforcement" target="_blank">GSA Schedule 84</a>. Your chosen integrator will help your agency choose the right PACS products and services, according to your agency’s preferred GSA purchasing vehicle(s).</li>
	</ul>
	</li>
	<li>Want to learn more about GSA Schedules? Training is available: <a href="https://www.gsa.gov/buying-selling/products-services/security-protection/training-for-security-protection" target="_blank">On-demand GSA Schedules Training</a>. For help with GSA Schedules, email the GSA National Customer Service Center at NCSCcustomer.service@gsa.gov or call 1-800-488-3111.</li>
  </ul>
  </td>
</tr>
 
</table>


{% include alert-info.html content="If at any time you have PACS procurement questions, contact the GSA IT Customer Service at ITCSC@gsa.gov or call 1-855-482-4348." %}



## Why Can We Buy Only GSA-Approved Products and Services?
[GSA’s FIPS 201 Evaluation Program](https://www.idmanagement.gov/fips201/){:target="_blank"} tests all GSA-listed PACS products, topologies, and services for compliance with FIPS 201-2 requirements. Purchasing products listed on the GSA APL ensures product compliance with FIPS 201-2, secure operations, and interoperability.   

## What Other GSA Resources Can Help Us?
- [GSA Schedules - General Information](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/schedule-buyers){:target="_blank"}
- [GSA Schedules - Tools and Resources](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/we-are-here-to-help){:target="_blank"}
- [GSA Multiple Awards Schedule (MAS)](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/schedules-news-and-updates){:target="_blank"}
- [GSA Schedule 70]( https://www.gsa.gov/technology/technology-purchasing-programs/it-schedule-70){:target="_blank"} offers GSA-approved integrators and HSPD-12 products and services.  
- [GSA Schedule 84](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/list-of-gsa-schedules/schedule-84security-fire-law-enforcement){:target="_blank"} offers FIPS 201-compliant, GSA-approved, HSPD-12 PACS components and services.
- [GSA’s eBuy](https://www.ebuy.gsa.gov/ebuy/){:target="_blank"} RFQ online system enables you to post requirements, obtain quotes, and issue orders electronically. 
- Approved [Certified System Engineer ICAM PACS (CSEIP) List]( https://www.securetechalliance.org/activities-cseip-registry/){:target="_blank"}.  Agencies must use FIPS 201-approved integrators and other contractors. The "lead designer" for FIPS 201-approved integrators must possess a Certified System Engineer ICAM PACS (CSEIP) certification or be certified by another federally recognized certification program.    

The next section, *[Training]({{site.baseurl}}/train/)*, outlines PACS personnel roles and responsibilities and lists relevant training and certification programs.

# Training

Specialized training is essential for Physical Access Control System (PACS) technical leads and team members. This page describes roles, responsibilities, and training opportunities. 


* [Technical Roles and Responsibilities](#technical-roles-and-responsibilities)
* [Recommended Technical Training](#recommended-technical-training)
* [Training Opportunities](#training-opportunities)


## Technical Roles and Responsibilities

PACS project teams consist of both agency employees and contractors. Teams include an IT Architect, Engineers, Technicians, Operators, System Administrators, Physical Security Specialists, Facility Managers, a variety of technical services team members, etc. The table below describes the most common PACS technical roles: 

| Technical Role | Responsibilities |
|:------|:-------------| 
| IT Architect | Defines the project's technical activities according to the project scope and requirements; conducts further analysis and design, as required; and directs the implementation of a PACS solution. |
| Engineer | Makes configuration recommendations and advises the IT Architect about enterprise-wide network improvements, PACS hardware and software optimization, testing, deployment, and maintenance.|
| Technician | Installs, administers, and maintains network and system components. |
| Operator | Uses physical security functions, such as setting access privileges or taking actions to resolve system-generated events and alarms.|


{% include alert-info.html content="IT Architects, Engineers, and Operators may be federal employees and/or contractors. Technicians are typically contractors." %}

{% include alert-info.html content="Teams also include a PACS Project Manager, Procurements Official or Specialist, project management specialists, budget analysts, lawyer(s), etc." %}


## Recommended Technical Training

| Role | Recommended Training |
|:------|:-------------| 
| IT Architects| Must be knowledgeable about the [GSA PACS APL](https://www.idmanagement.gov/approved-products-list-pacs-products/){:target="_blank"} and the manufacturers' solutions for PACS. Should be knowledgeable about Federal Government and agency-specific policies, standards, and guidance documents to make design recommendations related to a PACS implementation. Architects must possess a current [Certified System Engineer ICAM PACS (CSEIP) certification](https://www.securetechalliance.org/activities-certified-system-engineer-icam-pacs-training-and-certification-program/){:target="_blank"}{:rel="noopener noreferrer"} or other similar, federally recognized certification in order to implement a PACS solution.|
| Engineers| May hold a [CSEIP](https://www.securetechalliance.org/activities-certified-system-engineer-icam-pacs-training-and-certification-program/){:target="_blank"}{:rel="noopener noreferrer"} certification or other similar, federally recognized certification. Engineers may optionally complete PACS products' manufacturers' training (for example, PACS APL products) related to the PACS implementation. Should be knowledgeable about Federal Government and agency-specific policies, standards, and guidance documents related to enterprise networks and an PACS implementation. |
| Technicians | Should complete PACS products' manufacturers' training (i.e., PACS APL products) related to the PACS solution implementation.| 
| Operators | Should complete tailored training in Federal Government policies and standards related to PACS. Completing PACS products' manufacturers' (i.e., PACS APL products) certification related to the PACS implementation is recommended.|

{% include alert-info.html content="Agencies must specify their requirements for specific roles, responsibilities, and training in their Request for Information (RFI) (that is, request for contractor qualifications statements) and Statement of Work (SOW)." %}


## Training Opportunities

{% include alert-info.html content="Agencies that plan to initiate a PACS Project should include line items for related employee training in their annual training plans and annual training budgets." %}

### Department of Homeland Security - Interagency Security Committee
The [Interagency Security Committee](https://www.dhs.gov/interagency-security-committee){:target="_blank"}{:rel="noopener noreferrer"} developed a series of free, self-paced, [online training courses](https://www.dhs.gov/interagency-security-committee-training){:target="_blank"}{:rel="noopener noreferrer"} that provide an overview of facility security standards, processes, and practices.

### Equipment Manufacturers
[GSA PACS APL](https://www.idmanagement.gov/approved-products-list-pacs-products/){:target="_blank"}{:rel="noopener noreferrer"} PACS manufacturers whose products are listed on the GSA PACS APL offer product-specific courses for Operators and Technicians directly or through authorized service providers. Operators and Technicians may obtain certifications for completing some series of courses.

>**Note:** Manufacturer training may not address unique operational requirements or site-specific configurations, so authorized service providers should conduct this training:  [GSA Schedule 84](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/list-of-gsa-schedules/schedule-84security-fire-law-enforcement){:target="_blank"}, and/or [GSA Schedule 70](https://www.gsa.gov/technology/technology-purchasing-programs/it-schedule-70){:target="_blank"}{:rel="noopener noreferrer"}. 

### Authorized Service Providers
Authorized service providers offer manufacturer training for installing, configuring, and maintaining PACSs: [GSA Schedule 84](https://www.gsa.gov/buying-selling/purchasing-programs/gsa-schedules/list-of-gsa-schedules/schedule-84security-fire-law-enforcement){:target="_blank"}{:rel="noopener noreferrer"} and [GSA Schedule 70](https://www.gsa.gov/technology/technology-purchasing-programs/it-schedule-70){:target="_blank"}{:rel="noopener noreferrer"}. This training can be tailored to your agency, facility, implementation features, operational policies, and procedures. This training should be planned during the Procurements phase. 

### Industry Certifications
Industry certifications are vendor-neutral and standards-based. GSA requires that all work performed on approved PACS for GSA-managed facilities must be designed and installed by a Certified System Engineer for ICAM PACS (CSEIP).  The [CSEIP Program](https://www.securetechalliance.org/activities-certified-system-engineer-icam-pacs-training-and-certification-program/){:target="_blank"}{:rel="noopener noreferrer"} trains those who implement solutions related to OMB M-05-24 and OMB M-19-17.

Additional certification opportunities are offered by commercial vendors.

### GSA PACS Reverse Industry Day Conference (2018)

In 2018, GSA hosted a _PACS Reverse Industry Day_ conference that featured government and industry experts on a range of PACS topics. Event videos are available via the GSA YouTube channel: 

- [Morning Session](https://www.youtube.com/watch?v=r9X1XtrLjMg){:target="_blank"}
- [Afternoon Session](https://www.youtube.com/watch?v=bS8jdkW_WUI){:target="_blank"}{:rel="noopener noreferrer"}

# Lessons Learned

Federal agencies have shared these PACS lessons learned:

## Planning
- Identify all stakeholders upfront to include an Executive Sponsor.
- Designate staff to fill key roles, such as architects, engineers, and operators.
- Engage CIO/CISO representatives early. _Remember: A PACS is an IT System._
- As an IT system, a PACS must complete Certification and Accreditation and obtain an Authority to Operate before connecting to the network.
- Create, maintain, and share an integrated master schedule that presents project phases, tasks, resources, and dependencies.
- Establish a PACS component lifecycle management plan to help estimate hardware and software upgrades over the life of the system.  
- Build the cost of software licensing and system sustainment into your project budget.
- Work with facility engineers to identify constraints specific to your workplace, such as mandatory construction requirements. These constraints may limit solution offerings.
- Agencies moving towards FICAM-compliant PACS should consider the impact on the federal facility population when modernizing PACS assets. 
- Plan a standardized deployment strategy across locations.
- Legacy system hardware, such as credential readers, may not support FICAM compliant modes of operation. (FICAM Mode implies using PKI-based authentication mechanisms and online identity validation.) Review your system hardware capabilities after identifying desired authentication mechanisms to determine if upgrades are necessary. 
- Utilize legacy credentials and non-FICAM compliant modes of operation *only* in a migration strategy, not as the end state.
- Retire and phase out secondary, legacy credentials.
- Use your agency Identity Management System as the authoritative source for all user records in the PACS.
- Some PACS allow assignment of user access levels at the time of credential registration. Plan the method of assignment before provisioning/registration.
- Avoid acts of “omission” that create non-compliance. For example, procuring products listed on the Approved Products List (APL) but not correctly enabling FICAM Mode.
- Use a risk-based approach when selecting appropriate PIV authentication mechanisms for physical access to Federal government buildings and facilities, regardless of whether they are leased or government-owned. 
- Access points should not rely solely on an authentication mechanism that requires optional card features, as these features might not be available on all user-population cards (for example, on-card biometric comparison).
- Plan the PACS to meet the needs of the operating environment (for example, do not require three-factor authentication when only one factor is needed). 
- Understand that PKI is the foundation for high assurance PACS implementations.


## Procurements
- Do not procure non-compliant PACS technologies, such as proximity cards.
- Use consistent terms and recommended procurement language within requirements documents, specifications, SOWs, RFIs, RFPs, and RFQs. 
- Leverage agency subject matter experts to review SOWs, RFPs, and RFQs before releasing them for contractors' bids.
- Resolve SOW and PACS compliance issues as soon as they are recognized.
- Work closely with agency legal team members to define an SOW that contains unambiguous responsibilities for the integrator and appropriate cures for non-performance.
- Have your integrator provide copies of all relevant FIPS 201-2 compliance and functionality testing documentation.
- Specify personnel roles, responsibilities, and training requirements within the SOW (for example, all engineers must be CSEIP certified.)
- Ensure qualified professionals and/or subject matter experts review the design documents before releasing them for bid or formal contractor response. Consider hiring an SME capability to augment agency staff as a "buyer’s agent" during these activities.
- Consider looking for evidence of qualified and/or registered personnel certifying the proposed solution (submittals) before approval or notice to proceed.


## Operations
- Define clear processes and procedures to support the remedy of system incidents (for example, a failed credential reader).  Be sure to identify key support personnel and expected levels of support. 
- Perform regular system maintenance and patching of the PACS components. Establish clear procedures for testing upgrades prior to widespread deployment, and develop "roll-back" procedures in the event they are required. 
- Ensure the PACS is configured and maintained to operate in FICAM Mode. 
- Work with your IT Department to ensure your PACS can perform online certificate validation. Credential validation should take place at or near the time of authentication. If your PACS is limited to offline certificate validation, manually load CRLs and certificate trust lists into the PACS daily.
- Provision only assured identities from an agency authoritative source into your PACS.
- For any PIV credential that becomes invalid (expired, certificates placed on CRL, etc.), the PACS administrator may wish to disable the credential in the PACS immediately, rather than waiting for it to happen automatically through the routine credential validation process.  Consider disabling identity and credential records rather than removing them to retain audit data that might be needed at a later time (for example, employee misconduct investigations).
- To protect privacy, remove all PII from PACS endpoints.
- Audit expected system functionality on a regular basis.  Minimally, verify that access points are challenging the correct number and type of authentication factors. Consider using test credentials which have expired or been revoked to further ensure correct operation.


## Training
- Create and maintain a training plan that formally documents training requirements.
- Provide role-specific training to agency stakeholders, such as HR, IT, or Security.

The next section, [Standards, Policies, and Guidance]({{site.baseurl}}/standards/) lists relevant public law, policies, regulations, standards, guidance, and publications relevant to PACSs.

# Standards, Policies, and Guidance

- [Public Law](#public-law)
- [Policies](#policies)
- [Regulations](#regulations)
- [Standards](#standards)
- [Guidance and Best Practices](#guidance-and-best-practices)
- [Other Relevant Publications](#other-relevant-publications)

## Public Law

[Federal Information Security Modernization Act (FISMA) of 2014](https://www.dhs.gov/fisma){:target="_blank"}, Public Law No: 113-283. 

## Policies

OMB Circular A-130, ["Managing Information as a Strategic Resource"](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/circulars/A130/a130revised.pdf){:target="_blank"}, July 2016.

OMB M-05-24, ["Implementation of Homeland Security Presidential Directive (HSPD) 12 – Policy for a Common Identification Standard for Federal Employees and Contractors"](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2005/m05-24.pdf){:target="_blank"}, August 5, 2005.

OMB M-19-17, [Enabling Mission Delivery through Improved Identity, Credential, and Access Management](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}, May 21, 2019.

E.O. 13800, ["Strengthening the Cybersecurity of Federal Networks and Critical Infrastructure"](https://www.whitehouse.gov/presidential-actions/presidential-executive-order-strengthening-cybersecurity-federal-networks-critical-infrastructure/){:target="_blank"}, May 11, 2017.

E.O. 13636 and PPD-21 - ["DHS Factsheet: Improving Critical Infrastructure Cybersecurity and Critical Infrastructure Security and Resilience")](https://www.dhs.gov/publication/eo-13636-ppd-21-fact-sheet){:target="_blank"}, March 2013.

## Regulations

[_Federal Acquisition Regulation (FAR)_](https://www.acquisition.gov/browsefar){:target="_blank"}.

## Standards

[_Federal Identity, Credential, and Access Management (FICAM) Roadmap and Implementation Guidance_](https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/FICAM_Roadmap_and_Implem_Guid.pdf){:target="_blank"}, Version 2.0, Executive Office of the President (EOP) and Federal Chief Information Officers (CIO) Council, December 2, 2011.

[*Federal Public Key Infrastructure (FPKI) Security Controls Overlay of Special Publication 800-53 Security Controls for PKI Systems*](https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/FPKI-Overlay-of-SP-800-53.pdf){:target="_blank"}, v2.0.0, April 24, 2014.

[FIPS PUB 199, _Standards for Security Categorization of Federal Information and Information Systems_](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.199.pdf){:target="_blank"}, NIST, February 2004.

[FIPS PUB 200, _Minimum Security Requirements for Federal Information and Information Systems_](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.200.pdf){:target="_blank"}, NIST, March 9, 2006. 

[FIPS 201-2, _Personal Identity Verification (PIV) of Federal Employees and Contractors_](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.201-2.pdf){:target="_blank"}, NIST, August 2013.

[NIST SP 800-53, Revision 4, _Recommended Security Controls for Federal Information Systems and Organizations_](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r4.pdf){:target="_blank"}, April 2013.

[NIST SP 800-60, Volume 1, Revision 1, _Guide for Mapping Types of Information and Information Systems to Security Categories_](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-60v1r1.pdf ){:target="_blank"}, August 2008.

[NIST SP 800-60, Volume II, Revision 1, _Appendices to Guide for Mapping Types of Information and Information Systems to Security Categories_](http://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-60v2r1.pdf){:target="_blank"}, August 2008.

[NIST SP 800-73-4, _Interfaces for Personal Identity Verification_](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-73-4.pdf){:target="_blank"}, Parts 1 and 2, May 2015 (Updated February 8, 2016).

[NIST SP 800-116, Revision 1, _Guidelines for the Use of PIV Credentials in Facility Access_](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-116r1.pdf){:target="_blank"}, June 2018. 

[NIST SP 800-171, Revision 1, _Protecting Controlled Unclassified Information in Nonfederal Information Systems and Organizations_](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171r1.pdf){:target="_blank"}, December 2016.

## Guidance and Best Practices

[_Best Practices for Planning and Managing Physical Security Resources: An Interagency Security Committee Guide_](https://www.dhs.gov/sites/default/files/publications/isc-planning-managing-physical-security-resources-dec-2015-508.pdf){:target="_blank"}, Interagency Security Council (ISC), December 2015.

[_Enabling Strong Authentication with PIV Cards: Public Key Infrastructure (PKI) in Enterprise Physical Access Control Systems (E-PACS) Recommended Procurement Language for RFPs_](https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/Procurement-Language-1.1.0.pdf){:target="_blank"}, v1.1.0, GSA, February 24, 2015.

[_PACS Customer Ordering Guide (v2.0)_](https://www.gsa.gov/cdnstatic/General_Supplies__Services/Guide_to_PACS_v2%2006-12-2018.pdf){:target="_blank"}, GSA Schedule 84 - Security, Fire, & Law Enforcement, June 2018.

[_Personal Identity Verification (PIV) in Enterprise Physical Access Control Systems (E-PACS)_](https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/piv-in-epacs.pdf){:target="_blank"}, Interagency Security Committee (ISC), Version 3.1, March 26, 2014.

[_Personal Identity Verification Interoperability for Issuers_](https://www.idmanagement.gov/wp-content/uploads/sites/1171/uploads/piv-i-for-issuers.pdf){:target="_blank"}, Version 2.0.1, July 27, 2017.

[_The Risk Management Process for Federal Facilities: An Interagency Security Committee Standard_](https://www.dhs.gov/sites/default/files/publications/isc-risk-management-process-2016-508.pdf){:target="_blank"}, ISC, 2nd Edition, November 2016.

## Other Relevant Publications

["Federal Building Security:
Actions Needed to Help Achieve Vision for Secure, Interoperable Physical Access Control"](https://www.gao.gov/products/GAO-19-138){:target="_blank"}, Government Accountability Office (GAO), December 20, 2018. 

# Glossary

{% include alert-info.html content="NIST SP-800-116, Revision 1, \"Guidelines for the Use of PIV Credentials in Facility Access\" <a href=\"https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-116r1.pdf\" target=\"_blank\">Appendix G </a> contains additional PACS-related terms and definitions." %}


### Access Control 

The process of granting or denying specific requests to: 

1. obtain and use information and related information processing services; and 
2. enter physical facilities, such as federal buildings, military establishments, and border crossing entrances.


### Access Point 

An access point can be a door, turnstile, or other physical barrier, where granting access can be electronically controlled.


### Authentication

The process of establishing confidence in the authenticity and validity of a person’s identity.


### Authentication Factors	

Authentication systems are often categorized by the number of factors that they incorporate. The three factors often considered as the cornerstone of authentication are:

- Something you know (for example, a password)
- Something you have (for example, an ID badge or a cryptographic key)
- Something you are (for example, a thumb print or other biometric data)

Authentication systems that incorporate all three factors are stronger than systems that only incorporate one or two of the factors.	


### Authorization

Grants access to only the resources a person needs to perform a job.  A person with an authentic, high-assurance credential (PIV or CAC) will not have access to all resources.  In a large enterprise with thousands of employees and contractors needing access to hundreds of different access points, attempting to manage authorization manually is costly, time consuming, and error-prone.


### Biometric 

A measurable, physical characteristic or personal behavioral trait used to recognize the identity, or verify the claimed identity, of an applicant. Facial images, fingerprints, and iris image samples are all examples of biometrics.


### BIO

A [FIPS 201](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.201-2.pdf){:target="_blank"} authentication mechanism that is implemented by using a fingerprint or iris images data object sent from the PIV credential to the PACS and which is matched to the credential holder’s live scan.


### BIO-A

A [FIPS 201](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.201-2.pdf){:target="_blank"} authentication mechanism in which the BIO authentication mechanism is performed in the presence of an attendant who supervises the use of the PIV credential and the submission of the PIN and the sample biometric by the credential holder.


### BIO(-A)

A shorthand used to represent both BIO and BIO-A authentication mechanisms.


### Credential

A collection of information about a person, attested to by an issuing authority. A credential is a data object, such as a certificate, that can be used to authenticate the credential holder. One or more data object credentials may be stored on the same physical memory device, such as a PIV card.


### Credential Validation

The process of determining if a credential is valid, which can include the following requirements:
* The credential was legitimately issued.
* The credential's activation date has been reached.
* The credential has not expired.
* The credential has not been tampered with.
* The credential has not been suspended or revoked by the issuing authority.


### Certificate Revocation List 

A list of revoked public key certificates created and digitally signed by a Certification Authority.	


### Identity Management System (IDMS) 

Identity management system comprised of one or more systems or applications that manages the identity verification, validation, and issuance process.


### Identity Registration

The process of making a person’s identity known to the PIV system, associating a unique identifier with that identity, and collecting and recording the person’s relevant attributes into the system.


### Identity Verification 

The process of confirming or denying that a claimed identity is correct by comparing the credentials (something you know, something you have, something you are) of a person requesting access with those previously proven and stored in the PIV credential or system and associated with the identity being claimed.


### Interoperability 

The quality of allowing any government facility or information system to verify a credential holder’s identity using the credentials on the PIV credential, regardless of issuer.


### OCC-AUTH

A two-factor authentication mechanism that uses secure messaging and an on-credential comparison of credential holder fingerprint(s).

### Physical Access Control System
An electronic system that controls the ability of people to enter a protected area, by means of authentication and authorization at access control points.


### PKI-AUTH

A PIV authentication mechanism that is implemented by an asymmetric key challenge/response protocol using the PIV
Authentication certificate and key.


### PKI-CAK

A PIV authentication mechanism that is implemented by an asymmetric key challenge/response protocol using the Card Authentication certificate and key.


### Provisioning

Specifying for each identity both the credential used (for example, a PIV, CAC, or PIV-I card) and the privileges granted to access specific resources (for example, a particular facility, door, or access point), and ensuring that complex set of rules is enforced.


### SYM-CAK

The SYM-CAK is an authentication mechanism based on the optional symmetric card authentication key. As the name implies, the purpose of the SYM-CAK authentication mechanism is to authenticate the credential and thereby the credential holder.


### Validation

The process of determining that an identity credential was legitimately issued and is still valid, that is, the credential has not expired or been revoked.
