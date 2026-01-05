# EmailJS Setup Guide for Portfolio Contact Form

## Overview
Your portfolio contact form is now integrated with EmailJS, which will send form submissions directly to your email: **rajeswarareddy254@gmail.com**

## Setup Instructions

### Step 1: Create EmailJS Account
1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" (it's FREE!)
3. Sign up using your Gmail account: **rajeswarareddy254@gmail.com**

### Step 2: Add Email Service
1. After logging in, go to **"Email Services"** in the dashboard
2. Click **"Add New Service"**
3. Select **"Gmail"** as your email service
4. Click **"Connect Account"** and authorize with your Gmail
5. Give it a name like "Portfolio Contact"
6. Click **"Create Service"**
7. **IMPORTANT**: Copy the **Service ID** (something like "service_abc123")

### Step 3: Create Email Template
1. Go to **"Email Templates"** in the dashboard
2. Click **"Create New Template"**
3. Use this template configuration:

**Template Name**: Portfolio Contact Form

**Subject**: New Portfolio Contact from {{from_name}}

**Content (HTML)**:
```html
<h2>New Contact Form Submission</h2>
<p><strong>From:</strong> {{from_name}}</p>
<p><strong>Email:</strong> {{from_email}}</p>
<p><strong>Message:</strong></p>
<p>{{message}}</p>
<hr>
<p><i>This email was sent from your portfolio contact form</i></p>
```

**To Email**: {{to_email}}

4. Click **"Save"**
5. **IMPORTANT**: Copy the **Template ID** (something like "template_xyz789")

### Step 4: Get Public Key
1. Go to **"Account"** → **"General"**
2. Find your **Public Key** (something like "abcdefg123456")
3. **IMPORTANT**: Copy this Public Key

### Step 5: Update Your Portfolio Code
Open `portfolio.html` and find these lines (around line 1150):

**Replace:**
```javascript
publicKey: "YOUR_PUBLIC_KEY", // Replace with your EmailJS public key
```
**With:**
```javascript
publicKey: "YOUR_ACTUAL_PUBLIC_KEY", // Paste the key you copied
```

**Replace:**
```javascript
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
```
**With:**
```javascript
emailjs.send('YOUR_ACTUAL_SERVICE_ID', 'YOUR_ACTUAL_TEMPLATE_ID', templateParams)
```

### Example (after replacement):
```javascript
// Initialize EmailJS
(function() {
    emailjs.init({
        publicKey: "abcdefg123456", // Your actual public key
    });
})();

// In the form submission:
emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

## Step 6: Save & Test
1. Save your `portfolio.html` file
2. Open it in a browser
3. Go to the Contact section
4. Fill out the form with test data
5. Click "Send Message"
6. You should see:
   - Button changes to "Sending..." with spinner
   - Success message: "✅ Message sent successfully!"
   - Email arrives in **rajeswarareddy254@gmail.com**

## Features Implemented

✅ **Email Delivery**: Messages sent to rajeswarareddy254@gmail.com
✅ **Loading State**: Button shows spinner while sending
✅ **Success Feedback**: Green success message on send
✅ **Error Handling**: Red error message if sending fails
✅ **Form Reset**: Form clears after successful send
✅ **Auto-hide Messages**: Success/error messages disappear after 5 seconds

## Troubleshooting

### If emails aren't sending:
1. Check browser console (F12) for errors
2. Verify all three IDs are correct (Public Key, Service ID, Template ID)
3. Make sure you authorized Gmail in EmailJS
4. Check EmailJS dashboard for error logs

### If you see "Failed to send message":
1. Double-check your Public Key is correct
2. Verify Service ID and Template ID match exactly
3. Ensure Gmail service is properly connected in EmailJS

## Free Tier Limits
- EmailJS Free Plan: **200 emails/month**
- Perfect for a portfolio site!

## Need Help?
- EmailJS Documentation: https://www.emailjs.com/docs/
- Check the browser console for detailed error messages

---
**Note**: Keep your Public Key safe but know it's designed to be used in client-side code. The Service ID and Template ID should also be kept in your code.
