# The HIPAA Security Rule

Outlines national security standards intended to protect health data created, received, maintained, or transmitted electronically.
**Note:** All safeguards noted below were sourced explicitly from the [HIPAA Administrative Simplification document](https://www.hhs.gov/sites/default/files/hipaa-simplification-201303.pdf) on the HHS website.

## 3 Parts to the HIPAA Security Rule

1. Administrative Safeguards
2. Technical Safeguards
3. Physical Safeguards

### Administrative Safeguards

The administrative components are essential when implementing a HIPAA compliance program; you are required to:

+ Assign a privacy officer
+ Complete a risk assessment annually
   + [Health IT Gov's Security Risk Assessment Tool](https://www.healthit.gov/topic/privacy-security-and-hipaa/security-risk-assessment-tool)
   + [NIST's HIPAA Security Rule Toolkit - Depreciated](https://csrc.nist.gov/projects/security-content-automation-protocol/hipaa)
+ Implement employee training
+ Review policies and procedures
+ Execute Business Associate Agreements (BAAs) with all partners who handle protected health information (PHI)
   + If you are using AWS, get a BAA with Amazon:
      + https://aws.amazon.com/health/healthcare-compliance/
      + https://aws.amazon.com/compliance/hipaa-eligible-services-reference/
      + https://aws.amazon.com/blogs/security/accept-a-baa-with-aws-for-all-accounts-in-your-organization/
      + https://docs.aws.amazon.com/artifact/latest/ug/managingagreements.html
   + If you are using Google Apps Suite and/or Google Compute Engine get a BAA with Google:
      + https://cloud.google.com/security/compliance/hipaa-compliance/
      + https://cloud.google.com/security/compliance/hipaa/
      + [Accept the HIPAA Business Associate Amendment](https://support.google.com/a/answer/3407074)
   + If you are using Office365 and/or Azure, get a BAA with Microsoft:
      + https://www.microsoft.com/en-us/trustcenter/compliance/compliance-overview
      + https://www.microsoft.com/en-us/TrustCenter/Compliance/HIPAA
      + http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=52&Language=1
   + Get a BAA with any other SaaS/PaaS/IaaS provider that you will use that will have ePHI transmitted through and stored within them. Review the[HHS's Article "Guidance on HIPAA and Cloud Computing"](https://www.hhs.gov/hipaa/for-professionals/special-topics/cloud-computing/index.html) further discusses the conduit exception.
   + Note: There is "conduit exception” rule that was defined as part of the HIPAA Omnibus Final Rule.
      The HIPAA Omnibus Final Rule explicitly states that the mere conduit exception is intended to include organizations that deal with “any temporary storage of transmitted data incident to such transmission.” It continues to define the distinction between transmission (including incidental storage associated with such transmission) and ongoing storage. The difference between those two situations “is the transient vs. persistent nature of” the opportunity to access PHI. **So a BAA isn't needed for the United States Postal Service, Couriers, and their electronic equivalents, and Internet service providers (ISPs).** The [HHS's Article "Guidance on HIPAA and Cloud Computing"](https://www.hhs.gov/hipaa/for-professionals/special-topics/cloud-computing/index.html) further discusses the conduit exception.
      

## Required vs. Addressable Specifications

Some HIPAA implementation specifications are “required,” and others are “addressable.”
**Required implementation specifications must be implemented no matter what.**

**Addressable implementation specifications must be implemented, and exceptions are only acceptable if it is unreasonable to implement the specification** (for example: extremely cost prohibitive or technically infeasible). All exceptions must be thoroughly documented with evidence of why addressable specification implementation was unreasonable.
**It is important to remember that an addressable implementation specification is not optional.**

**Honestly, you should implement the addressable implementation specifications, they are best practice security controls**

### Technical Safeguards

Technical safeguards outline what your application must do while handling PHI.

While there are both required and addressable elements to these safeguards, you should implement them all. Addressable elements (such as automatic logoff) are just best practices.

#### Access Control Requirements

+ Unique User Identification **(required)**: Assign a unique name and/or number for identifying and tracking user identity.
+ Emergency Access Procedure (required): Establish (and implement as needed) procedures for obtaining necessary ePHI during an emergency.
+ Automatic Logoff **(addressable)**: Implement electronic procedures that terminate an electronic session after a predetermined time of inactivity.
+ Authentication **(required)**: Implement procedures to verify that a person or entity seeking access to ePHI is the one claimed.
+ Encryption and Decryption **(addressable)**: Implement a mechanism to encrypt and decrypt ePHI in transit and at rest (ideally FIPS-140-1 and FIPS-140-2 compliant encryption algorithms should be utilized).

#### Transmission Security

+ Integrity Controls (addressable): Implement security measures to ensure that electronically transmitted ePHI is not improperly modified without detection until disposed of.
+ Encryption and Decryption **(addressable)**: Implement a mechanism to encrypt and decrypt ePHI in transit and at rest (ideally FIPS-140-1 and FIPS-140-2 compliant encryption algorithms should be utilized).

#### Audit and Integrity

+ Audit Controls (required): Implement hardware, software, and/or procedural mechanisms that record and examine activity in information systems that contain or use ePHI.
+ Mechanism to Authenticate ePHI (addressable): Implement electronic mechanisms to corroborate that ePHI has not been altered or destroyed in an unauthorized manner.

### Physical Safeguards

The Physical Safeguards have to do with who has access to PHI data and how that access is managed. Much of the Physical Safeguard requirements that developers need to worry about are handled by HIPAA compliant hosting companies (such as AWS, Rackspace, etc.).

Other parts of the Physical Safeguards are handled by your internal rules around who can and can't access PHI.

#### Facility Access Controls

+ Contingency Operations (addressable): Establish (and implement as needed) procedures that allow facility access in support of data restoration under the disaster recovery and emergency operations plan in the event of an emergency.
+ Facility Security Plan (addressable): Implement policies and procedures to safeguard the facility and the equipment therein from unauthorized physical access, tampering, and theft.
+ Access Control and Validation Procedures (addressable): Implement procedures to control and validate a person’s access to facilities based on their role or function, including visitor control and control of access to software programs for testing and revision.
+ Maintenance Records (addressable): Implement policies and procedures to document repairs and modifications to the physical components of a facility which are related to security (e.g., hardware, walls, doors, and locks).

#### Device and Media Controls

+ Disposal (required): Implement policies and procedures to address the final disposition of ePHI, and/or the hardware or electronic media on which it is stored. Please see the [HHS's Article "Guidance to Render Unsecured Protected Health Information Unusable, Unreadable, or Indecipherable to Unauthorized Individuals"](https://www.hhs.gov/hipaa/for-professionals/breach-notification/guidance/index.html)
+ Media Re-Use (required): Implement procedures for removal of ePHI from electronic media before the media are made available for re-use.
+ Accountability (addressable): Maintain a record of the movements of hardware and electronic media and any person responsible therefore.
+ Data Backup and Storage (addressable): Create a retrievable, exact copy of ePHI, when needed, before movement of equipment.

#### Workstation Security

+ Workstation Security (required): Implement physical safeguards for all workstations that access ePHI, to restrict access to authorized users.
+ Workstation Use (required): Implement policies and procedures that specify the proper functions to be performed, how those functions are to be performed and the physical attributes of the surroundings of a specific workstation or class of workstation that can access ePHI.
