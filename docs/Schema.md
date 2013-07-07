# MedMinder Schema Definitions

* Revision 1 - 2013-Jul-06 - Initial Revision - Matt Schneeberger
* Revision 2 - 2013-Jul-06 - Formatting - Matt Schneeberger
* Revision 3 - 2013-Jul-06 - Added User / Role Management, Formatting - Matt Schneeberger

## User / Role Management

**Note**: All fields are NOT NULL unless otherwise specified

### User table (Users)
Basic information about users

* `ID` int(11) Primary Key
* `UserName` varchar(50) Unique
* `Password` varchar(255)
* `Email` varchar(255)
* `Role` int(11) {Value defined in `auth.php` configuration, see Project Roles}
* `LastLogin` varchar(25)
* `LoginHash` varchar(255)
* `Created` int(11) DEFAULT 0 {Unix timestamp}
* `Updated` int(11) DEFAULT 0 {Unix timestamp}

### Profile fields table (ProfileFields)
Profile field definitions, allowing us to dynamically add or remove profile fields that are displayable

* `FieldName` varchar(64) Primary Key
* `FieldType` varchar(16)
* `FieldSize` int(11)
* `Enabled` bit(1) DEFAULT 1

### Profile values table (Profile)
Profile field values

* `FieldName` varchar(64) REFERENCES ProfileFields(FieldName)
* `UserID` int(11) REFERENCES Users(ID)
* `Value` text
* `Visibility` int(11) {0=Private,1=Patients Only,2=Public}
* `PRIMARY KEY(FieldName,UserID)`

### Relationship mappings (RelationshipMap)
Simple Caregiver Relationship definitions

* `PatientID` int(11) REFERENCES Users(ID) "User ID of patient in the relationship"
* `CaregiverID` int(11) REFERENCES Users(ID) "User ID of caregiver in the relationship"
* `WriteAccess` bit(1) DEFAULT 1 "Boolean field indicating if the caregiver has write access to the patient's records"
* `PRIMARY KEY(PatientID,CaregiverID)`

## Drugs - FDA

[Drugs@FDA Data Files](http://www.fda.gov/Drugs/InformationOnDrugs/ucm079750.htm)

**Note** All fields are NOT NULL unless otherwise specified

### Application Documents (AppDoc)
Document addresses or URLs to letters, labels, reviews, Consumer Information Sheets, FDA Talk Papers, and other types.

* `AppDocID int(4) Primary Key`
* `ApplNo varchar(6)`
* `SeqNo varchar(4)`
* `DocType varchar(50)`
* `DocTitle varchar(100), nulls`
* `DocURL varchar(200), nulls`
* `DocDate datetime(8), nulls`
* `ActionType varchar(10)`
* `DuplicateCounter int(4), nulls`

### Application Document Type Lookup (AppDocType_Lookup)
Type of document that is linked, which relates to the AppDoc table.

* `AppDocType varchar(50) Primary Key`
* `SortOrder int(4)`

### Application (Application)
Application number and sponsor name.

* `ApplNo varchar(6) Primary Key`
* `ApplType varchar(5) (A=ANDA, N=NDA, B=BLA)`
* `SponsorApplicant varchar(50)`
* `MostRecentLabelAvailableFlag bit(1)`
* `CurrentPatentFlag bit(1)`
* `ActionType varchar(10)`
* `Chemical_Type varchar(3), nulls`
* `Therapeutic_Potential varchar(2), nulls`
* `Orphan_Code varchar(1), nulls`

### Document Type Lookup (DocType_Lookup)
Supplement type code and description to the application number.

* `DocType  varchar(4) Primary Key`
* `DocTypeDesc varchar(50), nulls`

### Product (Product)
This table contains the products included in each application. Includes form, dosage, and route.

* `ApplNo varchar(6) Primary Key`
* `ProductNo varchar(3) Primary Key`
* `Form varchar(255), nulls`
* `Dosage varchar(240), nulls`
* `ProductMktStatus tinyint(1) (1=prescription, 2=OTC, 3=discontinued, 4=tentative approval) Primary Key`
* `TECode varchar(100), nulls`
* `ReferenceDrug bit(1) (0=not RLD, 1=RLD, 2=TBD)`
* `Drugname varchar(125), nulls`
* `Activeingred varchar(255), nulls `

### Product_TECode
Therapeutic Equivalence Code for Products.

* `ApplNo varchar(6) Primary Key`
* `ProductNo varchar(3) Primary Key`
* `TECode varchar(50)`
* `TESequence int(4) Primary Key`
* `ProdMktStatus tinyint(1) Primary Key`

### Supplements (RegActionDate)
Approval history for each application. Includes supplement number and dates of approval.

* `ApplNo  varchar(6) Primary Key`
* `ActionType varchar(10)`
* `InDocTypeSeqNo varchar(4) Primary Key`
* `DuplicateCounter int(4) Primary Key`
* `ActionDate datetime(8), nulls`
* `DocType varchar(4), nulls`
* `ChemicalType_Lookup`
* `ChemicalTypeID int(4) Primary Key`
* `ChemicalTypeCode varchar(3)`
* `ChemicalTypeDescription varchar(200)`
* `ReviewClass_Lookup`
* `ReviewClassID int(4) Primary Key`
* `ReviewCode varchar(1)`
* `LongDescritption varchar(100), nulls`
* `ShortDescription varchar(100)`

## Scheduling / Calendars / Reminders

To Be Determined
