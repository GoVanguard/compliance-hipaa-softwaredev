# The Software Developers Guide to HIPAA Compliance

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

The fines and charges are broken down into 2 major categories: “Reasonable Cause” and “Willful Neglect”. Reasonable Cause ranges from $100 to $50,000 per incident and does not involve any jail time. Willful Neglect ranges from $10,000 to $50,000 for each incident and can result in criminal charges.

**HIPAA violation categories and their respective penalty amounts are outlined in the chart below:**

![hipaa violations summary](https://dg80atg7s3qsy.cloudfront.net/blog/img/hipaa-violations.png)

Source: HHS, Federal Register.gov

**What sort of penalties are we talking about? Check out this chart with fines levied in years past:**

![hipaa fines table](https://dg80atg7s3qsy.cloudfront.net/blog/img/hipaa-fines.png)

Source: HHS, Case Examples and Resolution Agreements

Looking at this chart we can conclude that HHS does not like people storing unencrypted PHI on mobile devices. What we don’t see yet are fines levied against business associates.

2014 is the first year where business associates will be audited and fined. Smart money says that the first fines levied against business associates will be passed down toward the end of this year.

If these fines make you nervous, then this might be a good time to revisit your decision about whether your application needs to be HIPAA compliant or not.

The good news is that not every PHI breach ends in a fine. If you can show that you have made a reasonable effort to comply with HIPAA then you may not be dinged.

## The Four Rules of HIPAA

Like the four horsemen, these are the significant pieces that govern what you do and how you do it.

+ HIPAA Privacy Rule
+ HIPAA Security Rule
+ HIPAA Enforcement Rule
+ HIPAA Breach Notification Rule

**Developers mostly need to focus on the Technical and Physical safeguards outlined in the Security Rule.**

## Important Terms to Know

### Protected Health Information (PHI)

You hear this term non-stop when dealing with applications that can store health information. It's typically called PHI although some parts of the law refer to digitally-stored PHI as ePHI. We'll stick with PHI for consistency.

PHI is any information in a medical record that can be used to identify an individual, and that was created, used, or disclosed in the course of providing a health care service, such as a diagnosis or treatment.

In other words, PHI is information in your medical records, including conversations between your doctors and nurses about your treatment. PHI also includes your billing information and any medical information in your health insurance company's computer system.

Some examples of PHI:

+ Billing information from your doctor
+ Email to your doctor's office about a medication or prescription you need.
+ Appointment scheduling note with your doctor's office
+ An MRI scan
+ Blood test results
+ Phone records

Examples of non-PHI data:

+ Number of steps in a pedometer
+ Number of calories burned
+ Blood sugar readings w/out personally identifiable user information (PII) (such as an account or user name)
+ Heart rate readings w/out PII

### The Difference Between Protected Health Information and Consumer Health Information

So how do you know if you’re dealing with protected health information (PHI) or consumer health information? The test is pretty simple: if your device or application stores, records or transmits the user’s personally-identifiable health data held in the app or device to a covered entity (see below) then you are dealing with protected health information and need to be HIPAA compliant.

If you are building a wearable device or application that collects health information but does not plan on sharing it with a covered entity at any point in time, then you do not need to be HIPAA compliant.

For example, the Nike Fuel Band is not HIPAA compliant because it does not track data considered protected health information because you can't transmit that data from the device to a covered entity.

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

Examples of Potential Business Associates Include:

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

In contrast, these folks are NOT Business Associates:

+ Covered Entity’s Workforce
+ Individuals or companies with minimal and incidental exposure to health information, such as a telephone company, electrician, etc.
+ Companies that act as a conduit for PHI, such as the postal service, UPS, private couriers, etc.

# Who certifies HIPAA compliance?
## The short answer is no one.

Unlike PCI, no one can “certify” that an organization is HIPAA compliant. The Office for Civil Rights (OCR) from the Department of Health and Human Services (HHS) is the federal governing body that determines the state of compliance through a thorough audit. HHS does not endorse or recognize the “certifications” made by private organizations.

There is an evaluation standard in the Security Rule § 164.308(a)(8), and it requires you to perform a periodic technical and non-technical evaluation to make sure that your security policies and procedures meet the security requirements outlined in the rule. HHS doesn’t care if the evaluation is performed internally or by an external organization—just as long as it happens. Ideally, it is best to use the [HHS HIPAA Audit Protocol](https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/audit/protocol/index.html).

That said, being evaluated by an independent, third-party auditor is still an excellent idea. Even though it's not official, you should still do it. Many great companies can help you with this process. For example, [GoVanguard](https://govanguard.io) offers HIPAA Risk Assessments that can let you know how you stack up to the requirements outlined by the legislation. Again, be sure that the independent, third-party auditor at least runs your organization through the [HHS HIPAA Audit Protocol](https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/audit/protocol/index.html); if they aren't then most likely the HIPAA Risk Assessment being offering isn't comprehensive. 

**Note** Even if you get a "certification" from an external organization, then it should be more appropriately referred to as an attestation. The HHS can still come in and find a security violation, third-party audits and "certifications"(attestations) do not absolve you from your legal obligations under the Security Rule.

**Note**
There is an information security framework (not a regulatory law) called [HITRUST CSF](https://hitrustalliance.net/hitrust-csf/) that is closely aligned with HIPAA specifications and in many cases more concretely builds upon HIPAA. Leaders of healthcare providers, payers, and third-party vendors formed the HITRUST alliance to regulate the interpretation of inconsistent views on data security standards. HITRUST, in partnership with other industry leaders, created the Common Security Framework (CSF) to be the premier model for the future of healthcare compliance validation. Because HIPAA mandates are so convoluted, HITRUST CSF Certification gives an additional rationale for businesses to uphold a higher standard in regards to the value of data. HITRUST CSF Certification is a certification that is established after a rigorous third-party audit that recognizes complete compliance with HIPAA regulations and more.

