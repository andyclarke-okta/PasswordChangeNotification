# **Password Change Notification** 


## <span style="text-decoration:underline;">Overview</span>

End user security is a major concern for all CIAM customers. Account takeover is can be mitigating by notifying an end users when their password has changed in the event that it was performed without their knowledge. Branding this notification across multiple application brands is important. Workflows can act on a password change and send a customized notice to the end user for confirmation.
The trigger event which intitiates the workflows is a User Password Changed event on the Okta Identity Platform. This occurs whether the user initiates a self service password change or a password is set by admistraive action.
A customized HTML email template is built which shall substitute user and event context dynamically. Email is sent via a Workflows Connector, in this sample we are usaing O365, or any API accessible email service.

## Before you get Started / Prerequisites

Before you get started, here are the things you’ll need:



*   Access to an Okta tenant with Okta Workflows enabled for your Org 
*   Email service, in this sample O365 is used. Configure O365 Workflow Connector.


## Setup Steps



1. Select flow titled “Password Change Notification”
    1. Make sure the child flow "[O365] Send Email HTML" found in the folder is selected. This child flow shall handle the email send.
2. Select flow titled "[O365] Send Email HTML".
    1. Selector Connector for "Office 365 Mail" card
3. Ensure that both flows are turned on.


## Testing this Flow

The easiest way to test a flow is to perform a password change from the Okta End User Dashboard



1. Login into the Okta Dashboard with your test account
2. Navigate to the Settings UI.
3. Perform a Change Password operation.
4. Go to the email client for your test user and inspect notification email


## Limitations & Known Issues



*   None