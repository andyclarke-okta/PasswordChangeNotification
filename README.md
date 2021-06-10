# **Password Change Notification** 


## <span style="text-decoration:underline;">Overview</span>

End user security is a major concern for all CIAM customers. Account takeover can be mitigating by notifying an end users when their password has changed,thereby alerting them in the event that it was performed without their knowledge. Branding this notification across multiple application brands is important. Workflows can act on a password change event and send a customized notice to the end user.
The trigger event which intitiates the workflows is a User Password Changed event on the Okta Identity Platform. This occurs whether the user initiates a self service password change or a password is set by administrative action.
A customized HTML email template is built which shall substitute user and event context dynamically. Email is sent via a Workflows Connector, in this sample we are using O365, or any API accessible email service will work.

## Before you get Started / Prerequisites

Before you get started, here are the things you’ll need:



*   Access to an Okta tenant with Okta Workflows enabled for your Org 
*   Email service, in this sample Twilio Sendgrid is used. Configure Sendgrid Workflow Connector.


## Setup Steps


1. Some setup is required in Sendgrid to successfully execute this flow.
	1. Create a test Sendgrid Account if you do not already have one;
	https://signup.sendgrid.com/?utm_source=nurture&cvo&utm_medium=sggetademoformlv&utm_campaign=sgdemoty
	2. This integration reguires a Sendgrid APIkey with Full Access Permisions. This will be used to configure the Sendgrid connector in Workflows.
	https://sendgrid.com/docs/ui/account-and-settings/api-keys/
	3. This integration reguires a Sender Authentication for a domain or a single sender. In this example, a Single Sender Verification is used.
	https://sendgrid.com/docs/ui/sending-email/sender-verification/
	4. This integration reguires a Dynamic Transactional Template that supplies the formatting and the substitution variable for the email. The substitution variables will be filled with data passed in from Okta Workflows.
	https://sendgrid.com/docs/ui/sending-email/how-to-send-an-email-with-dynamic-transactional-templates/#design-a-dynamic-transactional-template
	Sendgrid has both a graphical template design tool and a code based template design tool. In this example i used the code based design tool.
	Here is Dynamic Transactional Template used for this example.
	This template is used in the
	
```javascript
	
  <html>
    <head>
      <title></title>
    </head>
    <body>
<div style="background-color:#f3f1e8;margin:0">

 <table style="font-family:'proxima nova' , 'century gothic' , 'arial' , 'verdana' , sans-serif;font-size:14px;color:#5e5e5e;width:98%;max-width:600px;float:none;margin:0 auto" border="0" cellpadding="0" cellspacing="0" valign="top" align="left">

 <tbody>

 <tr align="middle">

 <td style="padding-top:30px;padding-bottom:32px"><img src="https://op1static.oktacdn.com/fs/bco/4/fs0x6s84s6XMV0DNz0h7" height="37" /></td>

 </tr>

 <tr bgcolor="#ffffff">

 <td>

 <table bgcolor="#edf3f8" style="width:100%;font-size:inherit;line-height:20px;padding:32px;border:1px solid;border-color:#f0f0f0" cellpadding="0">

 <tbody>

 <tr>

 <td style="color:#5e5e5e;font-size:22px;line-height:22px"> Password Changed </td>

 </tr>

 <tr>

 <td style="padding-top:24px"> Hi  {{fullName}} , </td>

 </tr>

 <tr>

 <td style="padding-top:24px"> The password was changed for your account; {{email}} . </td>

 </tr>

 <tr>

 <td style="padding-top:24px;font-size:18px;font-weight:600;color:#5e5e5e;line-height:24px"> Details </td>

 </tr>

 <tr>

 <td style="line-height:24px">When:  {{published}}
 <br /> From:  {{city}} , {{state}}  
 <br /> Performed by:  {{performedBy}}
 </td>

 </tr>

 <tr>

 <td style="padding-top:24px;font-size:18px;font-weight:600;color:#5e5e5e;line-height:24px"> Don't recognize this activity? </td>

 </tr>

 <tr>

 <td> Your account may have been compromised; we recommend reporting the suspicious activity to your organization. Please contact your system administrator immediately. </td>

 </tr>

 <tr>

 <td style="padding-top:24px"> If you experience difficulties accessing your account, send a help request to your administrator. </td>

 </tr>

 <tr>

 <td style="padding-top:24px"> The security of your account is very important to us and we want to ensure that you are updated when important actions are taken. </td>

 </tr>

 </tbody>

 </table> </td>

 </tr>

 </tbody>

 </table>

</div>
    </body>
  </html>

```



1. In Workflows Console Connections, create a Sendgrid connector using the APIkey created above.
2. Select flow titled “[Sendgrid] Password Change Notification”
    1. Selector Connector for "Sendgrid Custom API Action" card
3. Ensure that flow is turned on.


## Testing this Flow

The easiest way to test a flow is to perform a password change from the Okta End User Dashboard



1. Login into the Okta Dashboard with your test account
2. Navigate to the Settings UI on the Dashboard.
3. Perform a Change Password operation.
4. Go to the email client for your test user and inspect notification email


## Limitations & Known Issues



*   None