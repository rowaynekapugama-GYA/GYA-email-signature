# GYA Email Signature Assets — Vercel Deployment

## What's in this folder

**Shared assets** (used by all team member signatures):
- `icon-phone.png` — phone icon for contact row
- `icon-email.png` — envelope icon
- `icon-web.png` — globe icon
- `icon-pin.png` — location pin icon
- `google-partner-round.png` — circular Google Partner badge
- `smileox-round.png` — circular SmileOx badge

**Per-team-member assets:**
- `rowayne-flip.gif` + `rowayne-round.png` — Rowayne Kapugama
- `brett-flip.gif` + `brett-round.png` — Brett Dyson

**One asset you still need to upload separately:**
- `gya-main-logo.png` — the GYA logo currently on WordPress at
  https://generateyouraudience.com/wp-content/uploads/2023/04/gya-main-logo.png
  Download that and add it to the same Vercel bundle so everything lives together.

## Deploying to Vercel

Easiest option — deploy as a static site:

1. Create a new folder on your computer called `gya-signatures`
2. Drop all the files from this bundle into that folder
3. Also drop in `gya-main-logo.png` from the WordPress URL above
4. Install Vercel CLI if you don't have it: `npm i -g vercel`
5. From inside the folder, run: `vercel --prod`
6. Follow the prompts (link to your account, pick a project name like `gya-signatures`)
7. Vercel will give you a URL like `https://gya-signatures.vercel.app` — that's your CDN

Alternative — through the Vercel dashboard:
1. Go to vercel.com → New Project → Import (or drag-drop)
2. Upload the whole folder as a static deployment
3. Copy the deployed URL

## After deployment

Your images will live at URLs like:
```
https://gya-signatures.vercel.app/rowayne-flip.gif
https://gya-signatures.vercel.app/icon-phone.png
https://gya-signatures.vercel.app/google-partner-round.png
```

Open each signature HTML file (`gya-email-signature-v6.html` for Rowayne, 
`gya-email-signature-brett.html` for Brett) in a text editor and 
find-replace:

```
https://generateyouraudience.com/wp-content/uploads/2026/04
```

with your new Vercel URL, e.g.:

```
https://gya-signatures.vercel.app
```

Also find-replace the GYA logo reference:
```
https://generateyouraudience.com/wp-content/uploads/2023/04/gya-main-logo.png
```
with:
```
https://gya-signatures.vercel.app/gya-main-logo.png
```

Then copy the rendered preview into Gmail's signature settings as before.

## Why Vercel is a good choice for this

- Free tier is generous — email signature images load millions of times without hitting limits
- Global CDN — images load fast for recipients worldwide
- HTTPS by default — Gmail and Outlook require this
- Won't randomly disappear like some image hosts

## Adding future team members

Same process:
1. Send me the person's photo + name + title + contact details
2. I generate `firstname-flip.gif` and `firstname-round.png`
3. Drop the two new files into your Vercel folder
4. Redeploy (`vercel --prod` again)
5. The signature HTML just references the new URL

Shared assets never change — you only ever add per-person files.
