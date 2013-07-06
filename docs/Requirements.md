MedMinder Requirements Document
===============================

Revision 1 - 2013-Jul-06 - Initial Revision

Requirements
------------

1. Web Application for management and administration
2. Each Drug must track everything that a typical perscription label would contain, examples include:
	* Drug name, generic name (if applicable)
	* Script instructures (E.g. "Take one to two tablets by mouth every 6 hours as needed for pain.")
		* Parse this into a schedule and special provisions
	* Schedule (See requirement 3)
	* Certain times (E.g. Morning, evening, afternoon)
	* Special provisions (E.g. With food, before bed)
	* Warnings (E.g. No driving, no alcohol, special side effects)
3. Schedule medicines on any sort of reciprocating schedule:
	* Daily (E.g. Preventative drugs)
	* Weekly (E.g. Some steroids)
	* Every X hours (E.g. Hydrocodone)
	* Monthly (E.g. Special Birth-control)
4. Smart Daily Schedule
	* Group drugs that should be taken with food together around meal times
	* Evenly distribute drugs throughout the day
	* Respect the requirements of the drugs (E.g. in the morning/with breakfast, before bed, etc.)
	* Allow customization of time periods
		* Number of drug-taking times
		* Time-of-day for each period
5. Drug Calendars
	* Today/Daily
	* This Week/Weekly
	* Monthly
6. Drug Reminders
	* Notifications to take medicines, include basic information about each drug
