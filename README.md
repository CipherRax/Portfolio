# Configuring the "Contact Me" Section to Send Emails to a Specific Email

The "Contact Me" section in your portfolio website uses EmailJS, a free service that allows you to send emails directly from the frontend (your HTML/JavaScript) without needing a server or backend code. This is perfect for static sites hosted on GitHub Pages, Netlify, or Vercel. Emails will be sent to your specified email address (e.g., your personal or professional inbox) when someone submits the form.
EmailJS works by:

Connecting to an email service like Gmail, Outlook, or SendGrid.
Using a pre-defined email template.
Triggering the send via JavaScript when the form is submitted.

Important Notes:

EmailJS has a free tier (up to 200 emails/month). Upgrade if needed.
You'll need to verify your email/domain in EmailJS for security.
No coding backend required, but you'll need to set up an account.
The form data (name, email, message) will be inserted into your template and sent to your email (the "to" field in the template).

Step 1: Sign Up for EmailJS

Go to www.emailjs.com and click "Sign Up" (or "Get Started").
Create a free account using your email (this will be your admin email).
Verify your email address via the confirmation link sent to your inbox.
Once logged in, you'll land on the dashboard. Note your User ID (it's displayed in the dashboard or under Account > API Keys). This is a public key like user_abc123def456 – you'll use it in the code.

Step 2: Connect an Email Service (To Send Emails from Your Domain)
This sets up the "from" email (e.g., no-reply@yourdomain.com) and links to your email provider.

In the EmailJS dashboard, go to Email Services (left sidebar).
Click "Add New Service".
Choose your provider:

Gmail: Enter your Gmail address and an App Password (not your regular password). To get an App Password:

Go to your Google Account > Security > 2-Step Verification (enable if not already).
Under "App passwords," generate one for "Mail" and use it.


Other options: Outlook, Yahoo, SendGrid, etc. Follow the prompts to authenticate.


Save the service. You'll get a Service ID (e.g., service_xyz789). Copy this – you'll need it for the code.
Specify the "To" Email: In the service setup, you can set the default "to" email, but we'll override it in the template (Step 3) for more control. This "to" email is your specific inbox where messages will arrive (e.g., yourname@gmail.com).

## Step 3: Create an Email Template (To Customize the Received Email)
The template defines what the email looks like when it arrives in your inbox.

In the dashboard, go to Email Templates (left sidebar).
Click "Create New Template".
Choose a base (e.g., "Contact Us") or start blank.
Customize:

Subject: Something like "New Portfolio Contact: {{from_name}}".
To Email: Enter your specific email address (e.g., yourname@gmail.com). This is where all form submissions will be sent!
From Name/Email: Set to something like "Portfolio Contact Form" / "no-reply@yourdomain.com" (from your service).
Body (HTML or Plain Text): Use placeholders for form data. Example HTML body:
text<h3>New Message from {{from_name}}</h3>
<p><strong>From:</strong> {{from_name}} &lt;{{from_email}}&gt;</p>
<p><strong>Message:</strong></p>
<p>{{message}}</p>
<hr>
<p>This email was sent via EmailJS from your portfolio site.</p>

Placeholders: {{from_name}}, {{from_email}}, {{message}} will be replaced by the form inputs.




Save the template. Copy the Template ID (e.g., template_abc123). You'll need this for the code.
Test the Template: Use the "Send Test Email" button in the dashboard to send a sample to your specific email and verify it arrives.

## Step 4: Integrate into Your Website Code
