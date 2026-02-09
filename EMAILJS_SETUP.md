# EmailJS Setup Guide for Application Form

## Step 1: Create EmailJS Account
1. Go to https://www.emailjs.com/
2. Sign up for a free account
3. Verify your email

## Step 2: Add Email Service
1. Click on "Email Services" in the dashboard
2. Click "Add Service"
3. Select your email provider (Gmail recommended)
4. Follow the setup instructions to connect your email
5. Copy your **Service ID** (looks like: `service_xxxxxxxxxxxxx`)

## Step 3: Create Email Template
1. Go to "Email Templates" in the dashboard
2. Click "Create New Template"
3. Set the template name to something like "Application Form"
4. Use the template code below in the **HTML Content** section
5. Copy your **Template ID** (looks like: `template_xxxxxxxxxxxxx`)

## Step 4: Get Your Credentials
1. Click on the account icon (top right)
2. Go to "Account"
3. Copy your **Public Key** (looks like: `xxxxxxxxxxxxxxxxxxxxx`)

## Step 5: Update Your HTML File
Replace the following in your catering.html file:
- `YOUR_SERVICE_ID` → Your actual Service ID
- `YOUR_TEMPLATE_ID` → Your actual Template ID  
- `YOUR_PUBLIC_KEY` → Your actual Public Key (appears twice in the code)

```javascript
// Line with emailjs.init
emailjs.init('YOUR_PUBLIC_KEY');

// Inside emailjs.send()
emailjs.send(
    'YOUR_SERVICE_ID',
    'YOUR_TEMPLATE_ID',
    formData,
    'YOUR_PUBLIC_KEY'
);
```

---

## Email Template HTML
Copy this code into your EmailJS template's **HTML Content** section:

```html
<div style="font-family: system-ui, sans-serif, Arial; font-size: 12px">
  <div>A new application from <strong>{{fullName}}</strong> has been received. Kindly review at your earliest convenience.</div>
  <div
    style="
      margin-top: 20px;
      padding: 15px 0;
      border-width: 1px 0;
      border-style: dashed;
      border-color: lightgrey;
    "
  >
    <table role="presentation" style="width: 100%;">
      <tr>
        <td style="vertical-align: top">
          <div
            style="
              padding: 6px 10px;
              margin: 0 10px;
              background-color: aliceblue;
              border-radius: 5px;
              font-size: 26px;
            "
            role="img"
          >
            👤
          </div>
        </td>
        <td style="vertical-align: top; width: 100%;">
          <div style="color: #2c3e50; font-size: 16px">
            <strong>{{fullName}}</strong>
          </div>
          <div style="color: #cccccc; font-size: 13px">Application Received</div>
          <p style="font-size: 14px; margin: 10px 0;"><strong>Email:</strong> {{email}}</p>
          <p style="font-size: 14px; margin: 10px 0;"><strong>Phone:</strong> {{phone}}</p>
          <p style="font-size: 14px; margin: 10px 0;"><strong>Position Applied:</strong> {{position}}</p>
          <p style="font-size: 14px; margin: 10px 0;"><strong>Years of Experience:</strong> {{experience}}</p>
          <p style="font-size: 14px; margin: 10px 0;"><strong>Availability:</strong> {{availability}}</p>
        </td>
      </tr>
    </table>
  </div>

  <div style="margin-top: 20px; padding: 15px; background-color: #f5f5f5; border-radius: 5px;">
    <h3 style="color: #2c3e50; margin-top: 0;">Applicant Details</h3>
    
    <div style="margin-bottom: 15px;">
      <strong style="color: #2c3e50;">Key Skills:</strong>
      <p style="color: #555; margin: 5px 0; white-space: pre-wrap;">{{skills}}</p>
    </div>

    <div style="margin-bottom: 15px;">
      <strong style="color: #2c3e50;">Previous Work Experience:</strong>
      <p style="color: #555; margin: 5px 0; white-space: pre-wrap;">{{experienceDetails}}</p>
    </div>

    <div style="margin-bottom: 15px;">
      <strong style="color: #2c3e50;">References:</strong>
      <p style="color: #555; margin: 5px 0; white-space: pre-wrap;">{{references}}</p>
    </div>

    <div style="margin-bottom: 15px;">
      <strong style="color: #2c3e50;">Additional Information:</strong>
      <p style="color: #555; margin: 5px 0; white-space: pre-wrap;">{{additionalInfo}}</p>
    </div>
  </div>

  <div style="margin-top: 20px; padding-top: 15px; border-top: 1px solid lightgrey; font-size: 11px; color: #999;">
    <p>This is an automated email from EL ASADERO Application System.</p>
  </div>
</div>
```

---

## Testing
1. Make sure you've replaced all YOUR_XXX values with actual credentials
2. Open catering.html in your browser
3. Click "Apply Now" button
4. Fill out the application form
5. Click "Submit Application"
6. You should receive an email with the application details

## Troubleshooting
- **"Failed to submit"**: Check that your Service ID, Template ID, and Public Key are correct
- **Email not arriving**: Check your EmailJS dashboard for logs to see if there's an error
- **Variables not showing**: Make sure the variable names in the template (like {{fullName}}) exactly match the formData object keys in the JavaScript

