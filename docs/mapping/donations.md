# Donations

When a donation is made in the Pure Charity platform an Opportunity and a Campaign Member record will be created in the Salesforce instance following the mapping bellow.

## Campaign Member

The Campaign Member record will only be created at the first donation from the user to the campaign. The Contact will always refer to a Pure Charity user, so if the donation was made by a Giving Circle then the organizer admin will be the Contact.

Label | API Name | Type | Description
--- | --- | --- | ---
Status | `Status` | Picklist | "Backer"
Contact | `Contact` | Lookup(Contact) | Pure Charity User Contact
Campaign | `Campaign` | Lookup(Campaign) | Pure Charity Campaign

## Opportunity

Label | API Name | Type | Description
--- | --- | --- | ---
Pure Charity ID | `purecharity__Id__c` | Text(255) (External ID) (Unique Case Sensitive) | Internal Pure Charity ID
Opportunity Name | `Name` | Text(120) | A combination of Donor and Campaign name separated by a dash (i.e.: "John Doe - Some Fundraiser")
Primary Campaign Source | `Campaign` | Lookup(Campaign) | Pure Charity Campaign
Account Name | `Account` | Lookup(Account) | Donor Account
Primary Contact | `npsp__Primary_Contact__r` | Lookup(Contact) | Donor Contact (Nonprofit Starter Pack)
Opportunity Record Type | `RecordType` | Record Type | "Pure Charity Donation"
Amount | `Amount` | Currency(16, 2) | Donation amount
Lead Source | `LeadSource` | Picklist | "Fundraiser"
Stage | `StageName` | Picklist | "Closed Won"
Close Date | `CloseDate` | Date | Donation date
Probability (%) | `Probability` | Percent(3, 0) | "100%"
Type | `Type` | Picklist | "Recurring" for recurring donations and "One Time" for single donation
Anonymous Donation | `purecharity__AnonymousDonation__c` | Checkbox | `true` when donor decided to do not share his donation amount, email, and location with the fundraiser organizer
