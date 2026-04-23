# How to use SendGrid as SMTP relay in Profisee

Users must contact the departments or individuals in charge of their email system, their SendGrid environment, and their DNS administrator. Please contact the party or account administrator for your SendGrid account before beginning configuration.

To use SendGrid as a SMTP relay in Profisee:

## 1. SendGrid setup

1. Go to **Settings**in SendGrid, then **Sender Authentication**, then **Authenticate Your Domain**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibd213c0cfa7e858b.png)
2. Select a DNS host and whether you want to brand links for this domain, then click **Next**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3aa50849690e2ae9.png)
3. Enter your domain in the **Domain You Send From** field, then click **Next**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4bfbbfcf218fa9.png)
4. Under **Install DNS Records** you will see the required records that must be created by your DNS administrator. The records included below apply only to this example and will not be valid for all environments. Send those records to your Exchange or email administrator by either copy/pasting them in an email or clicking the **Send To A Coworker** tab.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i721048eb4cc58578.png)

## 2. Exchange/DNS/Email setup

### 2.1 SPF setup

1. Your company's exchange/email system admin should add SendGrid to your domain's SPF record and create the DKIM records based on the steps above. If you plan on using your root domain (ex. *contoso.com*) then you should amend your TXT record at root, i.e. your @TXT record: v=spf1 include:sendgrid.net -all

Your SPF record likely includes more **include** statements. Simply add the **include:sendgrid.net** to it like so:
v=spf1 include:somesender.com include:someothersender.com indlude:sendgrid.net -all

If you plan to use a subdomain like *notifications.contoso.com,* you must create/update the text record for the notifications subdomain instead of the @ TXT record.

### 2.2 DKIM Setup

1. Your company's exchange/email system admin should create the SendGrid provided CNAME records. If you plan on using the *notifications.contoso.com* or a similar domain, ensure that domain is used in SendGrid and that it will generate the required records.
2. Create 3 CNAME records; 1 for the subdomain and 2 more for the DKIM setup.

### 2.3 Verify Sender Authentication in SendGrid

1. Once the records have been created, click **Verify** in SendGrid. This will complete the setup.

### 2.4 Email API key in SendGrid

1. While still in SendGrid, click **Email API**, then **Integration Guide,** then **SMTP Relay**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i69d7c523f9c6c1aa.png)
2. Create and name the API key something meaningful (such as *Profisee Dev SMTP Key)* and save it somewhere secure. You will not be able to see it again during the configuration process.

## 3. Profisee SMTP Setup

1. Open Profisee FastApp Studio.
2. Navigate to the top right to **Settings**, then **System Settings**, scroll down to the **Notification** section, then input the email address you plan on using under the **Email From: account** field.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i860f8f4308704b21.png)

3. Under the Email Server section update the fields as below:

- **Email port number**: 587
- **Email server address**: smtp.sendgrid.net
- **Email use SSL**: true (*note: it's actually TLS*)
- **Email user name**: apikey
- **Email user password**: click inside the field and paste the SendGrid api key you generated in the previous step.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5940ef27990f58fa.png)

5. To test: go to your Profisee environment's **/rest** page, then scroll down to **Notifications**, expand the Post, click **Try it out,** update the example field below to include a user in your domain (@contoso.com in this example), then paste your Profisee API key under the **x-api-key** field and click **Execute**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iaba817660a68052b.png)

## Finish

Assuming all steps are completed correctly, the user in the example above will receive an email like the one below.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i969852cab44ef748.png)