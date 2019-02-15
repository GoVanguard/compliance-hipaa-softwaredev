# Does my app need to be HIPAA compliant?

This is the most important question you can ask, because HIPAA violations can result in some serious penalties.

### The Difference Between Protected Health Information (PHI) and Consumer Health Information (CHI)

So how do you know if you’re dealing with protected health information (PHI) or consumer health information? The test is pretty simple: if your device or application stores, records or transmits the user’s personally-identifiable health data held in the app or device to a covered entity (see below) then you are dealing with protected health information and need to be HIPAA compliant.

If you are building a wearable device or application that collects health information, but does not plan on sharing it with a covered entity at any point in time then you do not need to be HIPAA compliant.

**Below are some examples from the HHS to provide further guidance.**
Further examples can be found on the HHS website in their [Health App Use Scnarios & HIPAA](https://hipaaqsportal.hhs.gov/community-library/accounts/92/925889/Public/OCR-health-app-developer-scenarios-2-2016.pdf) document.

### App Scenario 1:
A consumer downloads a health app to their smartphone. They populate it with their own information. For example, the consumer inputs blood glucose levels and blood pressure readings they obtained herself using home health equipment.

**Does HIPAA Compliance Apply?** No. The developer is not creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity or another business associate. The consumer is using the developer’s app to help their manage and organize their information without any involvement of her health care providers.

### App Scenario 2:
A consumer downloads a health app to their smartphone that is designed to help them manage a chronic condition. They download data from their doctor’s EHR through a patient portal, onto their computer and then uploads it into the app. They also add their own information to the app.

**Does HIPAA Compliance Apply?** No. Developer is not creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity or another business associate. Instead, the consumer obtains health information from their provider, combines it with health information they input, and uses the app to organize and manage that information for their own purposes. There is no indication the provider or a business associate of the provider hired the app developer to provide or facilitate this service.

### App Scenario 3:
At the direction of their provider, a patient downloads a health app to their smartphone. The provider has contracted with app developer for patient management services, including remote patient health counseling, monitoring of patients’ food and exercise, patient messaging, EHR integration and application interfaces. Information the patient inputs is automatically incorporated into the provider's EHR.

**Does HIPAA Compliance Apply?** Yes, the developer is a business associate of the provider, because it is creating, receiving, maintaining and transmitting protected health information (PHI) on behalf of a covered entity. In this case, the provider contracts with the app developer for patient management services that involve creating, receiving, maintaining and transmitting PHI, and the app is a means for providing those services.

### App Scenario 4:
A consumer downloads to their smart phone a mobile PHR app offered by their health plan that offers users in its network the ability to request, download and store health plan records and check the status of claims and coverage decisions. The app also contains the plan’s wellness tools for members, so they can track their progress in improving their health. Health plan analyzes health information and data about app usage to understand effectiveness of its health and wellness offerings. App developer also offers a separate, directto-consumer version of the app that consumers can use to store, manage, and organize their health records, to improve their health habits and to send health information to providers.

**Does HIPAA Compliance Apply?** Yes, with respect to the app offered by the health plan, and no, when offering the direct-to-consumer app. Developer is a business associate of the health plan, because it is creating, receiving, maintaining or transmitting protected health information (PHI) on behalf of a covered entity. Developer must comply with applicable HIPAA Rules requirements with respect to the PHI involved in its work on behalf of the health plan. **But its “direct-to-consumer” product is not provided on behalf of a covered entity or other business associate, and developer activities with respect to that product are not subject to the HIPAA Rules.** Therefore, as long as the developer keeps the health information attached to these two versions of the app separate, so that information from the direct-to-consumer version is not part of the product offering to the covered entity health plan, **the developer does not need to apply HIPAA protections to the consumer information obtained through the “direct-to- consumer” app**.

### In Conlusion:
The majority of medical apps you see on Google Play and Apple iTune App Store don’t fall under HIPAA, as they’re usually intended for a patient’s personal use. These are apps for monitoring certain health aspects (weight, pulse, or glucose levels) or those to follow the medication schedule (unless this data is transmitted to a health plan server). Also, HIPAA Rules won’t apply if a patient downloads an app to send summary reports by a doctor’s recommendation. This is because the covered entity (the doctor) doesn’t enter into an agreement with a developer.

**Note:** If your app does augment or interface with a medical device (like a blood glucose monitor) then you should be considerate of the [FDA's guidelines and regulations pertaining to Mobile Medical Application](https://www.fda.gov/downloads/MedicalDevices/DeviceRegulationandGuidance/GuidanceDocuments/UCM263366.pdf) which is a seperate topic in itself that is outside the scope of this guide (at least currently).

**Lastly, if you are uncertain** use the [FTC's Mobile Health Apps Interactive Tool](https://www.ftc.gov/tips-advice/business-center/guidance/mobile-health-apps-interactive-tool) to figure out how your app is classified.
