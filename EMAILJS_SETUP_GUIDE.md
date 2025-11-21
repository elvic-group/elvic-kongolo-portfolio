# EmailJS Setup Guide for Contact Form

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Add an Email Service

1. In your EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the instructions to connect your email account
5. **Copy the Service ID** (you'll need this later)

## Step 3: Create an Email Template

1. Go to **Email Templates** in the dashboard
2. Click **Create New Template**
3. Use this template structure:

```
Subject: New Contact Form Message from {{first_name}} {{last_name}}

From: {{first_name}} {{last_name}}
Email: {{user_email}}

Message:
{{message}}
```

4. **Copy the Template ID** (you'll need this later)

## Step 4: Get Your Public Key

1. Go to **Account** → **General** in the dashboard
2. Find your **Public Key** (it looks like: `user_xxxxxxxxxxxxxxxxx`)
3. **Copy the Public Key**

## Step 5: Update Your Website Code

Open `index.html` and replace the following placeholders:

### Line ~2330 - Replace Public Key:
```javascript
emailjs.init('YOUR_PUBLIC_KEY'); // Replace with your actual public key
```
**Replace `YOUR_PUBLIC_KEY` with your actual public key**

### Line ~2348 - Replace Service ID and Template ID:
```javascript
emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', this)
```
**Replace:**
- `YOUR_SERVICE_ID` with your Service ID
- `YOUR_TEMPLATE_ID` with your Template ID

## Step 6: Test Your Form

1. Open your website
2. Fill out the contact form
3. Click Submit
4. Check your email inbox for the message

## Example Configuration

If your credentials are:
- Public Key: `user_abc123xyz`
- Service ID: `service_gmail`
- Template ID: `template_contact`

Your code should look like:
```javascript
emailjs.init('user_abc123xyz');
```

```javascript
emailjs.sendForm('service_gmail', 'template_contact', this)
```

## Template Variables

The form sends these variables to EmailJS:
- `{{first_name}}` - First name from the form
- `{{last_name}}` - Last name from the form
- `{{user_email}}` - Email address from the form
- `{{message}}` - Message from the form

Make sure your EmailJS template uses these exact variable names!

## Troubleshooting

**Form not sending?**
- Check browser console for errors (F12)
- Verify all three IDs are correct (Public Key, Service ID, Template ID)
- Make sure your email service is connected in EmailJS dashboard
- Check EmailJS dashboard for usage limits (free plan: 200 emails/month)

**Not receiving emails?**
- Check spam folder
- Verify template variable names match form field names
- Test the template in EmailJS dashboard

## Free Plan Limits

- 200 emails per month
- 2 email services
- 2 email templates

Need help? Contact EmailJS support or check their documentation at [https://www.emailjs.com/docs/](https://www.emailjs.com/docs/)

