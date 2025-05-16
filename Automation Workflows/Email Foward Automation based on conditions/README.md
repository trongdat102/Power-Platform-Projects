Fw emails based on the subject
1. Overview
This document outlines the email processing flow implemented. The flow is designed to send emails to different recipients based on a numerical value extracted from an incoming payload.

2. Business Requirements
Extract a numerical value from an incoming request.

Use a Switch control to determine the recipient based on the extracted number.

Send an email to the designated recipient with the extracted details.

Ensure error handling for unexpected values.

3. Technical Details
3.1. Trigger
The flow is triggered when an email arrives or an HTTP request is received.

Extracts a numerical identifier from the request body.

3.2. Data Extraction
A Compose action extracts the required number (Extract_Number) from the incoming payload.

Extracted value is stored as Extract_Number.

3.3. Switch Control
A Switch action evaluates Extract_Number and executes different email actions based on its value.

Cases:

1: Send an email to 1

2: Send an email to 2

3: Send an email to 3

4: Send an email to 4

5: Send an email to 5

If no match is found, the Default Case handles errors.

3.4. Email Configuration
Each email is sent using Office 365 Email (Send an Email V2).

Email content:

@{triggerOutputs()?['body/body']}

Email subject is dynamically retrieved from the trigger event: @triggerOutputs()?['body/subject'].

3.5. Error Handling
If Extract_Number is missing or invalid:

The Default Case logs the error and does not send an email.

An error message is logged: "Invalid input: No matching case found."


