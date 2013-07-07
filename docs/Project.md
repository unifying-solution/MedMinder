# MedMinder Project Information

* Revision 1 - 2013-Jul-06 - Initial Rivision - Matt Schneeberger

## Authentication

Authentication will use a variation on the [Simpleauth](http://fuelphp.com/docs/packages/auth/simpleauth/intro.html) module that ships with FuelPHP. We will extend this driver to add the relationships between patients and other roles.

Authentication will be very important, and most (if not all) of the relationships between users will require forms to comply with the Health Insurance Portability and Accoutabilty Act (HIPAA). [Read more about HIPAA](http://www.hhs.gov/ocr/privacy/)

## Roles

__Note__: There is currently only one application role. There has not been a need for any more.

* Patient - Basic level

## Caregiver/Physician Relationships

In order to provide flexibility for users of this application with special needs, there must be a mechanism for other users ("Caregivers") to access the records of "Patients". The role of "Caregiver" exists only conceptually, in that a normal user ("Patient") becomes a "Caregiver" when a relationship is defined between them and another patient.

### Option 1: Simple Relationships (Also Known As: "Caregiver Access")

With this method, every user is a Patient. Each Patient has read/write access to his own records.

Each "Patient" can grant read or read/write access to other users in what is known as a "Caregiver Relationship" or "Caregiver Access". This does not limit the access of the original Patient.

### Option 2: Advanced Relationships

__Note__: This is *exteremely* complicated to understand. This is actually the third revision of this standard after it was simplfied twice. It is _very likely_ that this will be scrapped in favor of the above simpler method.

A relationship exists between a parent user, and a child user. The child user _relates_ to a parent users in one of four ways:

* Child user is a __Patient__. Caregiver is granting read-only access to the patient's own medications/schedules, but is managing them on behalf of the patient.
* Child user is a __Patient+__. Caregiver is granting read/write access to the patient's own medications/schedules, allowing the patient to manage them in addition to the caregiver.
* Child user is a __Caregiver__. Patient is granting tead-only access to a caregiver.
* Child user is a __Caregiver+__. Patient is granting read/write access to a caregiver, usually to assist in managing medications/schedules.

### Example Relationships

These are examples of how patients and caregivers can use the system. Each situation is dependant on the patients' and caregivers' abilities and responsibilities.

#### Scenario 1 - Single Patient

This scenario is the simplest, a patient signs up with the system to assist with administering his or her own medicine.

#### Scenario 2 - Responsible Caregiver, Multiple Hands-off Patients

This scenario includes a responsible caregiver (in-home nurse, concerned family member, etc.) oversees the administering of the medicine. The caregiver signs up with the system, and will create accounts for each patient, creating "Patient" relationships for each person. Each patient has access to the system to view information, but cannot make changes to schedules. The caregiver is given the responsibility of ensuring the schedule of the drugs is correct.

#### Scenario 3 - Responsible Patient, Responsible Caregiver

In this scenario, the patient takes responsibility for the inputting of the drugs and scheduling. In addition, a second user (typically a spouse or relative) has access to the system to assist the patient. In this case, the "Patient" signs up with the system, and creates an account for the caregiver, as well as a relationship with the caregiver as "Caregiver" or "Caregiver+" depending on if they caregiver should have write access as well.
