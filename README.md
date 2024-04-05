# Receive Data From MS Forms and Create Syncro Ticket

Step 1) Make a form on MS Forms to collect required information
  - Users First Name
  - Users Surname
  - Job Role/Title
  - Department
  - Any special access such as email groups or role specific information
  - Requesters Name
  - Requesters Email Address

Step 2) Setup a flow similar to below

![image](https://github.com/bradhawkins85/MSFormsToSyncro/assets/15325110/64b1256a-3c09-45bd-9ed0-aa1b58cc188a)

The Sned Email step contains the following.

![image](https://github.com/bradhawkins85/MSFormsToSyncro/assets/15325110/47d92cab-7e61-46ec-90a5-eab1434086aa)

The email is sent via SMTP2Go using the requesters email address as the From address, this causes Syncro to log a ticket on behalf of the user.

The approval in the above flow is to allow me to validate the request before it is sent on to another staff member to create an application specific login. The conditions also check if the app has been requested and only generates an approval if it was requested. Example, Adobe Acrobat was requested for the new staff member (by selecting a radio button option), if I approve the request this is sent on to another staff member to log in to the Adobe account and create a user.

The parameters from the ticket containing all of the required information is then put in to a PowerShell script on the domain controller which has all of the logic for creating users, adding to groups, sync'ing to Azure etc.
