# Software Developers Guide to HIPAA Compliance

## Introduction
HIPAA, the [Health Insurance Portability and Accountability Act](http://en.wikipedia.org/wiki/Health_Insurance_Portability_and_Accountability_Act), was passed in 1996, and among other things, outlines the requirements for the management of, storage and transmission of protected health information (PHI) in both physical and digital form. Moreover, while the original legislation pre-dates the rise of the commercial Internet (and the iPhone by a decade), its rules govern the use of this special type of personal data by applications on the web and mobile devices.

With any twenty year old piece of legislation that was written in a world without smartphones, tablets, and heck, even webmail, HIPAA is full of requirements that are confusing and challenging, particularly for software developers who have to make sense of them as they relate to their product and the underlying technologies that we all use on a regular basis to build and deliver applications to our customer bases.

### 2013 Final Omnibus Rule Update
In September of 2013, the [Final Omnibus Rule Update](http://en.wikipedia.org/wiki/Health_Insurance_Portability_and_Accountability_Act#cite_note-33) was passed that amended HIPAA and greatly expanded the definition of who needed to be HIPAA compliant. Previously, only covered entities (such as doctors, hospitals, and insurers) were required to be HIPAA compliant. With the recent rule change, however, all entities that store, manage, record or pass Protected Health Information (we'll call it PHI from now on) to and from covered entities are also required to be HIPAA compliant. These entities, called Business Associates, who were previously exempt from HIPAA, now fall under its governance.

### Why this guide?
As you can imagine, complying with federal regulations around privacy and healthcare data is no small task. That's why we've created this guide—to help you wade through what you need to know about HIPAA compliance as it relates to your application and what steps you'll need to take to ensure you don't end up in violation of the law.

There is plenty to read about HIPAA guidelines, and if you want you can spend a good chunk of the rest of the year reading up on all the details. Therefore, we're not going to rewrite everything here. This guide is not meant to be comprehensive, but rather give you a framework and reference to help you understand the significant portions of the law that apply directly to the software you're developing for mobile, web and wearable applications.

### Who is this guide for?
If you're a developer building a web, mobile or wearable software application that deals in the collection, storage, or transmission of personally identifiable health information to covered entities like doctors this is for you. You'll get the ins and outs of HIPAA compliance guidelines and the steps you'll want to take to ensure you're within those guidelines in the development, hosting, and communication with your users.

From a breakdown of the terms and requirements to specific examples of HIPAA-covered activities, we've tried to give you what you need to understand the laws in plain language so that you can make the right decisions when developing your application.

Whether you decide that your application falls under HIPAA guidelines or not, this guide gives you the information you need to make that decision.

## Why is HIPAA Important?
### HIPAA Fines
HIPAA violations are expensive. The penalties for noncompliance are based on the level of negligence and can range from $100 to $50,000 per violation (or per record), with a maximum penalty of $1.5 million per year for violations of an identical provision. Violations can also carry criminal charges that can result in jail time.

Fines will increase with the number of patients and the amount of neglect. Starting with a breach where you didn’t know and, by exercising reasonable diligence, would not have known that you violated a provision. To the other end of the spectrum where a breach is due to negligence and not corrected in 30 days.

The fines and charges are broken down into 2 major categories: “Reasonable Cause” and “Willful Neglect.” Reasonable Cause ranges from $100 to $50,000 per incident and does not involve any jail time. Willful Neglect ranges from $10,000 to $50,000 for each incident and can result in criminal charges.

**HIPAA violation categories and their respective penalty amounts are outlined in the chart below:**

![hipaa violations summary](https://dg80atg7s3qsy.cloudfront.net/blog/img/hipaa-violations.png)
Source: HHS, Federal Register.gov

**What sort of penalties are we talking about? Check out this chart with fines levied in years past:**

![hipaa fines table](https://dg80atg7s3qsy.cloudfront.net/blog/img/hipaa-fines.png)
Source: HHS, Case Examples and Resolution Agreements

## The Four Rules of HIPAA
Like the four horsemen, these are the significant pieces that govern what you do and how you do it.
+ HIPAA Privacy Rule
+ HIPAA Security Rule
+ HIPAA Enforcement Rule
+ HIPAA Breach Notification Rule

**Software developers mostly need to focus on the Security Rule and Breach Notification Rule.**

## Important Terms to Know
### Protected Health Information (PHI)
PHI is any information in a medical record that can be used to identify an individual, and that was created, used, or disclosed in the course of providing a health care service, such as a diagnosis or treatment. Digitally-stored PHI is referred to as electronic Protected Health Information (ePHI).

In other words, PHI is information in your medical records, including conversations between your doctors and nurses about your treatment. PHI also includes your billing information and any medical information in your health insurance company's computer system.

**Some examples of PHI:**
+ Billing information from your doctor
+ Email to your doctor's office about a medication or prescription you need.
+ Appointment scheduling note with your doctor's office
+ An MRI scan
+ Blood test results
+ Phone records

**Examples of non-PHI data:**
+ Number of steps in a pedometer
+ Number of calories burned
+ Blood sugar readings w/out personally identifiable user information (PII) (such as an account or user name)
+ Heart rate readings w/out PII

### The Difference Between Protected Health Information and Consumer Health Information
So how do you know if you’re dealing with protected health information (PHI) or consumer health information? The test is pretty simple: if your device or application stores, records or transmits the user’s personally-identifiable health data held in the app or device to a covered entity (see below) then you are dealing with protected health information and need to be HIPAA compliant.

If you are building a wearable device or application that collects health information but does not plan on sharing it with a covered entity at any point in time, then you do not need to be HIPAA compliant. For example, the Nike Fuel Band is not HIPAA compliant because it does not track data considered protected health information because you can't transmit that data from the device to a covered entity.

### Covered Entity
A covered entity is anyone who provides treatment, payment, and operations in healthcare.

According to the U.S. Department of Health & Human Services (HHS) Healthcare Providers, Health Plans, and Healthcare Clearinghouses are all Covered Entities.

Covered Entities Include:
+ Doctor’s office, dental offices, clinics, psychologists,
+ Nursing home, pharmacy, hospital or home healthcare agency
+ Health plans, insurance companies, HMOs
+ Government programs that pay for healthcare
+ Health clearinghouses

### Business Associate
Simply put, a Business Associate is a vendor or subcontractor who has access to PHI.

A more legalese definition of a Business Associate is any entity that uses or discloses PHI on behalf of a Covered Entity. Furthermore, a Business Associate is any person who, on behalf of a Covered Entity, performs (or assists in the performance of) a function or activity involving the use or disclosure of PHI.

The vendors that we are talking about can be data storage or document storage services (doesn’t matter if they can view the PHI that they maintain), providers of data transmission services, portals or other interfaces created on behalf of Covered Entities that allow patients to share their data with the Covered Entity, and electronic health information exchanges.

If a Business Associate (vendor) delegates a covered function or activity to someone, then that entity is considered a subcontractor (who is also a Business Associate).

If a Covered Entity (customer) sends PHI through a vendor, and the vendor’s servers store this information, then they are considered a Business Associate and subject to the HIPAA Security Rule.

Unlike other laws (DMCA anyone?) there is no "safe harbor" clause with HIPAA. Just because you don't want to handle PHI doesn't opt you out of HIPAA compliance requirements.

**Examples of Potential Business Associates Include:**
+ Data processing firms or software companies that may be exposed to or use PHI
+ Medical equipment service companies handling equipment that holds PHI
+ Shredding and documentation storage companies
+ Consultants hired to conduct audits, perform coding reviews, etc.
+ Lawyers
+ External auditors or accountants
+ Professional translator services
+ Answering services
+ Accreditation agencies
+ e-prescribing services
+ Medical transcription services

**In contrast, these folks are NOT Business Associates:**
+ Covered Entity’s Workforce
+ Individuals or companies with minimal and incidental exposure to health information, such as a telephone company, electrician, etc.
+ Companies that act as a conduit for PHI, such as the postal service, UPS, private couriers, etc.

## Does my app need to be HIPAA compliant?
This is the most important question you can ask because HIPAA violations can result in some severe penalties.

### The Difference Between Protected Health Information (PHI) and Consumer Health Information (CHI)
So how do you know if you’re dealing with protected health information (PHI) or consumer health information? The test is pretty simple: if your device or application stores, records or transmits the user’s personally-identifiable health data held in the app or device to a covered entity (see below) then you are dealing with protected health information and need to be HIPAA compliant.

If you are building a wearable device or application that collects health information but does not plan on sharing it with a covered entity at any point in time, then you do not need to be HIPAA compliant.

**Below are some examples from the HHS to provide further guidance.**
Further examples can be found on the HHS website in their [Health App Use Scenarios & HIPAA](https://hipaaqsportal.hhs.gov/community-library/accounts/92/925889/Public/OCR-health-app-developer-scenarios-2-2016.pdf) document.

### App Scenario 1:
A consumer downloads a health app to their smartphone. They populate it with their information. For example, the consumer inputs blood glucose levels and blood pressure readings they obtained herself using home health equipment.

**Does HIPAA Compliance Apply?** No. The developer is not creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity or another business associate. The consumer is using the developer’s app to help manage and organize their information without any involvement of her health care providers.

### App Scenario 2:
A consumer downloads a health app to their smartphone that is designed to help them manage a chronic condition. They download data from their doctor’s EHR through a patient portal, onto their computer and then uploads it into the app. They also add their information to the app.

**Does HIPAA Compliance Apply?** No. The developer is not creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity or another business associate. Instead, the consumer obtains health information from their provider, combines it with health information they input and uses the app to organize and manage that information for their purposes. There is no indication that the provider or a business associate of the provider hired the app developer to provide or facilitate this service.

### App Scenario 3:
At the direction of their provider, a patient downloads a health app to their smartphone. The provider has contracted with app developer for patient management services, including remote patient health counseling, monitoring of patients’ food and exercise, patient messaging, EHR integration and application interfaces. Information the patient inputs are automatically incorporated into the provider's EHR.

**Does HIPAA Compliance Apply?** Yes, the developer is a business associate of the provider, because it is creating, receiving, maintaining and transmitting protected health information (PHI) on behalf of a covered entity. In this case, the provider contracts with the app developer for patient management services that involve creating, receiving, maintaining and transmitting PHI, and the app is a means for providing those services.

### App Scenario 4:
A consumer downloads to their smartphone a mobile PHR app offered by their health plan that offers users in its network the ability to request, download and store health plan records and check the status of claims and coverage decisions. The app also contains the plan’s wellness tools for members, so they can track their progress in improving their health. Health plan analyzes health information and data about app usage to understand the effectiveness of its health and wellness offerings. App developer also offers a separate, direct-to-consumer version of the app that consumers can use to store, manage, and organize their health records, to improve their health habits and to send health information to providers.

**Does HIPAA Compliance Apply?** Yes, concerning the app offered by the health plan, and no, when offering the direct-to-consumer app. The developer is a business associate of the health plan because it is creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity. The developer must comply with applicable HIPAA Rules requirements concerning the PHI involved in its work on behalf of the health plan. **But its “direct-to-consumer” product is not provided on behalf of a covered entity or other business associates, and developer activities concerning that product are not subject to the HIPAA Rules.** Therefore, as long as the developer keeps the health information attached to these two versions of the app separate, so that information from the direct-to-consumer version is not part of the product offering to the covered entity health plan, **the developer does not need to apply HIPAA protections to the consumer information obtained through the “direct-to-consumer” app**.

**Note:**
The majority of medical apps you see on Google Play and Apple iTunes App Store don’t fall under HIPAA, as they’re usually intended for a patient’s personal use. These are apps for monitoring certain health aspects (weight, pulse, or glucose levels) or those to follow the medication schedule (unless this data is transmitted to a health plan server). Also, HIPAA Rules won’t apply if a patient downloads an app to send summary reports by a doctor’s recommendation. This is because the covered entity (the doctor) doesn’t enter into an agreement with the developer.

**Note:** If your app does augment or interface with a medical device (like a blood glucose monitor) then you should be considerate of the [FDA's guidelines and regulations pertaining to Mobile Medical Application](https://www.fda.gov/downloads/MedicalDevices/DeviceRegulationandGuidance/GuidanceDocuments/UCM263366.pdf) which is a separate topic in itself that is outside the scope of this guide (at least currently). If you are uncertain use the [FTC's Mobile Health Apps Interactive Tool](https://www.ftc.gov/tips-advice/business-center/guidance/mobile-health-apps-interactive-tool) to figure out how your app is classified.

## Who certifies HIPAA compliance?
### The short answer is no one.

Unlike PCI, no one can “certify” that an organization is HIPAA compliant. The Office for Civil Rights (OCR) from the Department of Health and Human Services (HHS) is the federal governing body that determines the state of compliance through a thorough audit. HHS does not endorse or recognize the “certifications” made by private organizations.

There is an evaluation standard in the Security Rule § 164.308(a)(8), and it requires you to perform a periodic technical and non-technical evaluation to make sure that your security policies and procedures meet the security requirements outlined in the rule. HHS doesn’t care if the evaluation is performed internally or by an external organization—just as long as it happens. Ideally, it is best to use the [HHS HIPAA Audit Protocol](https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/audit/protocol/index.html).

That said, being evaluated by an independent, third-party auditor is still an excellent idea. Even though it's not official, you should still do it. Many great companies can help you with this process. For example, [GoVanguard](https://govanguard.io) offers HIPAA Risk Assessments that can let you know how you stack up to the requirements outlined by the legislation. Again, be sure that the independent, third-party auditor at least runs your organization through the [HHS HIPAA Audit Protocol](https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/audit/protocol/index.html); if they aren't then most likely the HIPAA Risk Assessment being offering isn't comprehensive. 

**Note** Even if you get a "certification" from an external organization, then it should be more appropriately referred to as an attestation. The HHS can still come in and find a security violation, third-party audits and "certifications"(attestations) do not absolve you from your legal obligations under the Security Rule.

**Note**
There is an information security framework (not a regulatory law) called [HITRUST CSF](https://hitrustalliance.net/hitrust-csf/) that is closely aligned with HIPAA specifications and in many cases more concretely builds upon HIPAA. Leaders of healthcare providers, payers, and third-party vendors formed the HITRUST alliance to regulate the interpretation of inconsistent views on data security standards. HITRUST, in partnership with other industry leaders, created the Common Security Framework (CSF) to be the premier model for the future of healthcare compliance validation. Because HIPAA mandates are so convoluted, HITRUST CSF Certification gives an additional rationale for businesses to uphold a higher standard in regards to the value of data. HITRUST CSF Certification is a certification that is established after a rigorous third-party audit that recognizes complete compliance with HIPAA regulations and more.

## Initial Considerations
### Does Using HIPAA Hosting Make My Application HIPAA Compliant?

**The short answer is no. HIPAA hosting alone does not make you HIPAA compliant.**

Compliance is determined by the adherence to the privacy and security rules outlined by HIPAA. HIPAA Hosting only addresses one aspect of those requirements. Hosting your application in a HIPAA compliant hosting environment such as Amazon AWS or Firehost does not make your application HIPAA compliant as they only address the physical safeguard requirements of the HIPAA security rule. You are still required to meet the administrative and technical specifications of the HIPAA Security Rule in order to be compliant.

### What Data Should Be Stored in HIPAA Compliant Hosting Environments?

Not all of your application data needs to exist in a HIPAA hosting environment. However, any PHI must be in a HIPAA compliant environment. Amazon has a pretty good [HIPAA compliance whitepaper](https://d0.awsstatic.com/whitepapers/compliance/AWS_HIPAA_Compliance_Whitepaper.pdf) that will help provide specific direction for AWS hosted environments.

### Network and application security

Ensuring your hosting environment is HIPAA compliant is only the first step. You must also implement network and application security best practices to protect your hosting environment.

Health information is a popular commodity for hackers. According to a recent [Information Week article](http://www.informationweek.com/healthcare/security-and-privacy/healthcare-it-security-worse-than-retail-study-says/d/d-id/1269207), each health record could be worth as much as $20 on the black market.

It's easy to imagine hackers trying to breach your servers when your application becomes popular. You need to be sure your HIPAA  hosting environment is locked down and secure from unauthorized access attempts.

### High-Availability and Redundancy

A good infrastructure design eliminates all single-point-of-failures. While running one web server and one database server may save you money in the short run, how much would it cost your business if that one web server goes offline causing the entire hosting environment to crumble?

It's best to design your hosting environment with at least 2 web servers behind a load balancer and 2 database servers on an active/passive failover setup.

Most environments are more complicated than just a 2-tier setup, so you must implement an infrastructure design best suited for your business. However, the point remains, high-availability and redundancy are crucial parts of your HIPAA compliant infrastructure.

## The HIPAA Security Rule

Outlines national security standards intended to protect health data created, received, maintained, or transmitted electronically.**Note:** All safeguards noted below were sourced explicitly from the [HIPAA Administrative Simplification document](https://www.hhs.gov/sites/default/files/hipaa-simplification-201303.pdf) on the HHS website.

**3 Parts to the HIPAA Security Rule**
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
   + Get a BAA with any other SaaS/PaaS/IaaS provider that you will use that will have ePHI transmitted through and stored within them. Review the [HHS's Article "Guidance on HIPAA and Cloud Computing"](https://www.hhs.gov/hipaa/for-professionals/special-topics/cloud-computing/index.html) further discusses the conduit exception.
   + Note: There is "conduit exception” rule that was defined as part of the HIPAA Omnibus Final Rule.
      The HIPAA Omnibus Final Rule explicitly states that the mere conduit exception is intended to include organizations that deal with “any temporary storage of transmitted data incident to such transmission.” It continues to define the distinction between transmission (including incidental storage associated with such transmission) and ongoing storage. The difference between those two situations “is the transient vs. persistent nature of” the opportunity to access PHI. **So a BAA isn't needed for the United States Postal Service, Couriers, and their electronic equivalents, and Internet service providers (ISPs).** The [HHS's Article "Guidance on HIPAA and Cloud Computing"](https://www.hhs.gov/hipaa/for-professionals/special-topics/cloud-computing/index.html) further discusses the conduit exception. 

#### Required vs. Addressable Specifications

Some HIPAA implementation specifications are “required,” and others are “addressable.”
Required implementation specifications must be implemented no matter what.
Addressable implementation specifications must be implemented, and exceptions are only acceptable if it is unreasonable to implement the specification (for example: extremely cost prohibitive or technically infeasible). All exceptions must be thoroughly documented with evidence of why addressable specification implementation was unreasonable.
**It is important to remember that an addressable implementation specification is not optional.**

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
## Additional Tips and Considerations

### Understanding Responsibilties and Regulations

+ If you are the product owner, take time to think about your use case for the app. Considering what information will be handled and stored and where in particular it will be stored is key if when you are dealing with PHI.
+ As previously stated, you should also consider what other regulations might play a prominent role in shaping your application’s design. The [FTC offers a tool](https://www.ftc.gov/tips-advice/business-center/guidance/mobile-health-apps-interactive-tool) to help you determine what will apply.

### Minimizing Risk and Exposure

+ Avoid accessing, displaying or storing data you don’t need. For example, if you don’t need full birthdate then don’t gather it. Any personal info you ask for should have a clear purpose.
+ Write and follow a clear privacy policy. This is important in any mobile app that collects user data, but especially so in health apps.
+ A highly effective and often overlooked way to avoid data security problems  is not to store it at all. Avoid storing or caching PHI whenever possible. Because of [how flash storage works](https://www.usenix.org/legacy/events/fast11/tech/full_papers/Wei.pdf) — e.g., wear leveling, block mapping — you can’t actually guarantee that data you write to system memory will be deleted.
+ Be careful with geolocation data. [HIPAA guidance](https://www.hhs.gov/hipaa/for-professionals/privacy/special-topics/de-identification/index.html) for what constitutes geographically identifying someone is information about any subdivision smaller than a state. Geolocation data about a patient can turn data that is fairly innocuous into PHI.
+ Local session timeout — your  app should certainly force re-authentication after inactivity. Consider your use-case for a good idea of how long that period should be.
+ Push notifications are often called out as a vulnerability. Ensure that PHI is never sent to push notifications that could easily be seen by someone other than the patient it pertains to.
+Data can leak out where it’s not intended. Avoid leaking PHI into backups and log files which are generally very loosely protected. SD cards in Android devices often have very loose access permissions and are particularly vulnerable as a result
+Mobile devices use a number of different protocols for sending information. SMS and MMS are not encrypted, so make sure they don’t contain PHI.
