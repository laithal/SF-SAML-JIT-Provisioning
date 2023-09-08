# Salesforce SAML JIT Provisioning

**Please Note:** I assume absolutely no responsibility for any of the code in this repository. Use at your own risk.

The sample Apex classes provided in this repo facilitate SAML Just-In-Time (JIT) provisioning based on data present in the SAML assertion. These classes cater to both user creation and updates depending on the information in the assertion. Moreover, they manage the user's permission set group assignments based on this data.

Below are the key components and details of the classes:

Base Class: Both AADJITHandler.cls (for Azure) and GoogleJITHandler.cls (for Google) extend from a common abstract base class, ensuring uniformity in some core functionalities.

PSG_DELETE_WHITE_LIST: This list is paramount in safeguarding manually assigned permission set groups within your org. Specifically, the class will only remove permission set group assignments that are whitelisted here.

Azure AD Claims: Do note that AADJITHandler.cls specifically uses custom Azure AD claims. It's essential to adapt the default claim types (http://schemas.xmlsoap.org/ws/2005/05/identity/claims/*) to resonate with your SAML provider's attributes.

A handy method to identify your claim types is by assessing the SAML response assertion through a SAML decoder, like:
Ping Identity SAML Decoder
Salesforce Claims: Salesforce has its own set of standard claims. However, it does not currently support Permission Set &/or Permission Set Group assignments. Here are Salesforce's accepted claims:

Salesforce JIT Requirements
Examples: User.Username, User.Email, User.LastName, User.ProfileId

In conclusion, it's imperative to ensure all claims and their respective implementations align with your organization's requirements.
