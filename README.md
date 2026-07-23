# Iva By SKR

A static website for Iva By SKR, a Petrichor Hotel in Hebbagodi, Electronic City, Bengaluru — built and ready to deploy.

## What's in this folder

- **`index.html`** — the whole site. A single HTML file that fetches `content/site-data.json` on load and renders every section (hero, rooms, amenities, gallery, reviews, booking links, FAQ, location, contact, chat widget) from it. No build step, no framework.
- **`content/site-data.json`** — all the actual text and data on the site (room details, amenities, reviews, FAQs, contact info, etc). Edit this file (or use the CMS below) to change what visitors see.
- **`admin/`** — a [Decap CMS](https://decapcms.org/) (formerly Netlify CMS) setup so the hotel owner can edit `site-data.json` through a form, without touching code or Git.
- **`images/`** — the hotel photography used across the room and gallery sections.

## Deploying it

### 1. Push to GitHub

This is already done — the repo is at `github.com/gaganakumarm/iva-by-skr-website` — but here are the commands for reference if you ever need to redo this from scratch:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/gaganakumarm/iva-by-skr-website.git
git push -u origin main
```

### 2. Deploy on Netlify

1. Sign up / log in at [netlify.com](https://netlify.com).
2. Click **"Import an existing project"** and connect your GitHub account.
3. Pick the `iva-by-skr-website` repo.
4. Leave the **build command blank** — there's no build step.
5. Set the **publish directory** to the repo root (`/` or just leave it empty).
6. Deploy. Netlify will give you a `*.netlify.app` URL right away.

### 3. Turn on Netlify Identity (so the CMS login works)

1. In the Netlify dashboard, go to **Site configuration → Identity → Enable Identity**.
2. Under registration settings, set it to **Invite only** — you don't want randoms signing themselves up as admins.

### 4. Enable Git Gateway

Still under **Identity settings**, turn on **Git Gateway**. This is what lets the CMS commit changes back to your GitHub repo on the owner's behalf, without them ever needing a GitHub account.

### 5. Invite the hotel owner

Under **Identity → Invite users**, enter the owner's email address. They'll get an email to set a password and log in.

### 6. Connect a custom domain

1. Buy the domain (any registrar is fine).
2. In Netlify, go to **Domain management** and add the custom domain.
3. Follow Netlify's DNS instructions (either point your registrar's nameservers at Netlify, or add the specific A/CNAME records it gives you).
4. HTTPS is automatic — Netlify provisions a free SSL certificate once DNS is pointed correctly. No extra setup needed.

## How the owner edits content

1. Go to `yourdomain.com/admin`.
2. Log in with the email/password from the invite.
3. Edit any section through the form fields — rooms, amenities, reviews, FAQ, contact details, etc.
4. Click **Publish**.
5. That's it — the site rebuilds automatically and the change is live in 1–2 minutes.

No code, no Git, no HTML.

## Before go-live

- Confirm the hotel phone and WhatsApp number in `site-data.json`.
- The enquiry form is intentionally backend-free: it prepares the guest's details and opens WhatsApp for the guest to send.
- Replace or add photography through `images/` and update the related entries in `site-data.json`.

## If something breaks

Every CMS save is just a Git commit under the hood. If a bad edit goes out (typo, broken layout, wrong price, whatever), go to the GitHub repo's commit history and revert to the previous commit — the site will rebuild from that version automatically. Nothing is ever really lost.
