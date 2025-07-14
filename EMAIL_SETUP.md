# Portfolio Email Setup Guide

This guide will help you set up email functionality for your portfolio contact form using Vercel and Gmail.

## Prerequisites

1. A Gmail account
2. Your portfolio deployed on Vercel

## Setup Steps

### 1. Generate Gmail App Password

1. Go to your Google Account settings: https://myaccount.google.com/
2. Navigate to **Security** > **2-Step Verification** (enable if not already enabled)
3. Go to **Security** > **App passwords**
4. Generate a new app password for "Mail"
5. Copy the 16-character password (this will be your `EMAIL_PASS`)

### 2. Configure Vercel Environment Variables

1. Go to your Vercel dashboard
2. Select your portfolio project
3. Go to **Settings** > **Environment Variables**
4. Add these variables:
   - `EMAIL_USER`: Your Gmail address (e.g., `yourname@gmail.com`)
   - `EMAIL_PASS`: The 16-character app password from step 1

### 3. Deploy Your Changes

1. Push your code changes to your GitHub repository
2. Vercel will automatically redeploy your site
3. The contact form will now send emails to your Gmail address

## File Structure

```
your-portfolio/
├── api/
│   └── contact.js          # Serverless function for email handling
├── package.json            # Dependencies
├── .env.example           # Environment variables template
└── index.html             # Updated contact form
```

## How It Works

1. User fills out the contact form
2. Form data is sent to `/api/contact` endpoint
3. Serverless function processes the data and sends email via Gmail
4. You receive the email in your Gmail inbox
5. User sees success/error message

## Testing

1. Fill out your contact form
2. Submit the form
3. Check your Gmail inbox for the message
4. You should receive an email with the form details

## Troubleshooting

### Common Issues

1. **App Password not working**: Make sure 2-Step Verification is enabled first
2. **Environment variables not set**: Double-check spelling and values in Vercel dashboard
3. **Email not sending**: Check Vercel function logs in the dashboard

### Email Format

You'll receive emails formatted like this:

```
Subject: Portfolio Contact: [Subject from form]

New Contact Form Submission

Name: John Doe
Email: john@example.com
Subject: Interested in your work
Message: Hi, I'd like to discuss a project with you...

This message was sent from your portfolio website.
```

## Security Notes

- Never commit your `.env` file with real credentials
- Use environment variables for all sensitive data
- App passwords are safer than regular passwords for automated systems

## Support

If you encounter issues:
1. Check Vercel function logs
2. Verify environment variables are set correctly
3. Test with a simple form submission
4. Check Gmail spam folder for test emails
