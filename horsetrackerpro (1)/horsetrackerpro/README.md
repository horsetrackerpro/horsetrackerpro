# HorseTrackerPro.com

## Your Complete Website Files

This folder contains everything you need to get HorseTrackerPro.com live.

### Files Included
- `index.html` — Your entire website
- `tips.json` — Daily tips data file (edit each morning)
- `tracked.json` — Daily tracked horses list (edit each morning)
- `README.md` — This guide

---

## NEW: Email Capture for Daily Tracked Horses List

Your site now captures emails so you can build a mailing list. Here's how it works:

### How Emails Are Captured
- Visitors enter their email on the homepage or Tracked Horses page
- Emails are stored in their browser's localStorage (they stay even if they close the site)
- **Important:** You need to collect these emails manually (see below)

### How to Collect Emails (Until You Set Up a Backend)

**Option 1 — Manual Collection (Free, Do This First):**
1. Ask a few trusted users to visit your site and enter their email
2. Open your site in a browser
3. Press **F12** → Click **Console** tab
4. Type this and press Enter:
   ```
   JSON.parse(localStorage.getItem('htp_emails') || '[]')
   ```
5. Copy the email list that appears
6. Paste into a spreadsheet or your email tool

**Option 2 — Google Form (Free, Recommended):**
1. Go to https://forms.google.com
2. Create a form with one field: Email
3. Get the form's "embed" code
4. Replace the email form in `index.html` with the Google Form embed
5. All submissions go straight to a Google Sheet automatically

**Option 3 — Email Service (Free Tier):**
- **Mailchimp** — Free up to 500 subscribers
- **Brevo (formerly Sendinblue)** — Free up to 300 emails/day
- **MailerLite** — Free up to 1,000 subscribers

Sign up → Create a signup form → Get the embed code → Replace the form in `index.html`

### How to Send the Daily Tracked Horses Email

Once you have emails collected:

1. **Copy your tracked horses** from `tracked.json`
2. **Paste into your email** (Gmail, Mailchimp, etc.)
3. **Send every morning** before racing (ideally 8-9am)

**Email template you can use:**
```
Subject: HorseTrackerPro Daily Tracked Horses — [Date]

Morning,

Here are today's tracked horses:

HIGH PRIORITY:
- Golden Promise (York 2:15pm) — 6/1 — Market support, trainer 4/8 at track
- Midnight Dash (Haydock 4:00pm) — 5/1 — Trainer targeting, work reports strong

MEDIUM PRIORITY:
- Coastal Wind (Sandown 3:30pm) — 9/2 — Dropped in class, jockey claims 3lb
- Silver Crest (Ascot 2:45pm) — 8/1 — Top jockey upgrade from apprentice

These are NOT official tips. They're horses showing positive signals.
Official tips + staking plan: https://horsetrackerpro.com/premium

Good luck,
HorseTrackerPro Team
```

---

## STEP-BY-STEP DEPLOYMENT GUIDE

### STEP 1: Create a GitHub Repository
1. Go to https://github.com and sign up (free)
2. Click the **+** button (top right) → **New repository**
3. Name it: `horsetrackerpro`
4. Make it **Public**
5. Click **Create repository**
6. Click **uploading an existing file**
7. Drag and drop ALL files from this folder into the box
8. Scroll down and click **Commit changes**

### STEP 2: Deploy to Cloudflare Pages (FREE)
1. Go to https://dash.cloudflare.com and sign up (free)
2. Click **Pages** in the left sidebar
3. Click **Create a project**
4. Click **Connect to Git**
5. Authorize Cloudflare to access your GitHub
6. Select your `horsetrackerpro` repository
7. Click **Begin setup**
8. **Project name:** horsetrackerpro
9. **Production branch:** main
10. **Framework preset:** None
11. **Build command:** (leave blank)
12. **Build output directory:** / (just a forward slash)
13. Click **Save and Deploy**

Your site will be live at: `https://horsetrackerpro.pages.dev`

### STEP 3: Connect Your Domain (horsetrackerpro.com)
1. In Cloudflare Pages, click your project
2. Go to **Custom domains** tab
3. Click **Set up a custom domain**
4. Enter: `horsetrackerpro.com`
5. Click **Continue**
6. Cloudflare will show you DNS records to add
7. Log into wherever you bought your domain
8. Change your nameservers to Cloudflare's nameservers
9. Wait 5-60 minutes
10. Your site is live at horsetrackerpro.com!

### STEP 4: Set Up Stripe Payments
1. Go to https://stripe.com and sign up (free)
2. Complete verification (upload ID, add bank account)
3. In Dashboard, go to **Products** → **Add product**
4. **Name:** Pro Punter Monthly
5. **Description:** HorseTrackerPro Premium Subscription
6. **Pricing model:** Standard pricing
7. **Price:** £14.99
8. **Billing period:** Monthly
9. Click **Save product**

#### To add the £9.99 intro offer:
1. Go to **Coupons** in Stripe Dashboard
2. Click **Create coupon**
3. **Name:** First Month Special
4. **Type:** Percentage off
5. **Percentage:** 33.36%
6. **Duration:** Once (applies to first payment only)
7. Click **Create coupon**
8. Go to **Payment Links** → **Create payment link**
9. Select your Pro Punter product
10. Toggle on **Apply a coupon** and select your coupon
11. Click **Create link**
12. Copy the link

### STEP 5: Add Your Stripe Link to the Website
1. Open `index.html` in your GitHub repo
2. Click the **pencil icon** to edit
3. Find: `https://buy.stripe.com/YOUR_PAYMENT_LINK_HERE`
4. Replace with your actual Stripe link
5. Commit the change

### STEP 6: Add Your Telegram Link
1. In `index.html`, find: `https://t.me/yourtelegramchannel`
2. Replace with your real Telegram handle
3. Commit the change

---

## DAILY WORKFLOW

### Every Morning Before Racing:

1. **Update Tips:** Edit `tips.json` on GitHub with today's 3 free tips
2. **Update Tracked Horses:** Edit `tracked.json` with today's tracked list
3. **Send Email:** Copy tracked horses from `tracked.json` and email your list
4. **Commit both files** — site updates automatically

---

## COSTS

| Item | Cost |
|------|------|
| Domain (you own) | £0 |
| Cloudflare Pages hosting | £0 |
| GitHub repository | £0 |
| Stripe account | £0 |
| Email (Google Forms) | £0 |
| **Total fixed monthly cost** | **£0** |

Stripe fees (only when you make a sale):
- UK cards: 1.5% + 20p per transaction
- £9.99 payment → you receive ~£9.64
- £14.99 payment → you receive ~£14.55

---

## SITE STRUCTURE

| Page | URL | What's There |
|------|-----|-------------|
| Home | `/` | Hero, stats, email capture form |
| Free Tips | `/` → click Free Tips | 3 daily horse tips |
| Tracked Horses | `/` → click Tracked | Daily tracked list + email capture |
| Premium | `/` → click Premium | Pricing, Stripe checkout |
| Results | `/` → click Results | P&L table, monthly stats |
| Blog | `/` → click Blog | Daily posts, previews, strategy |
