# Salesforce Agent Blazer — Website

Static site, ready to deploy on Vercel as-is (no build step needed).

## Folder structure

```
index.html                          → homepage (now includes the new event card)
events/agentblazer-unveiling.html   → the new event's dedicated page
assets/css/theme.css                → shared theme (colors, fonts, layout) used by both pages
assets/img/agentblazer-poster.jpg   → the event poster, shown on the event page
assets/img/speaker-santosh-rebello.jpg → cropped speaker photo for the speaker card
vercel.json                         → enables clean URLs (so the event page is reachable at
                                       /events/agentblazer-unveiling, no ".html" needed)
```

## What changed

- Added an "Agentblazer Unveiling" card to the **Upcoming** tab on the homepage (Aug 12 —
  placed first since it's the soonest date). The whole card links to the new event page.
- Built `events/agentblazer-unveiling.html` in the exact same theme as the homepage — same
  fonts, colors, nav, and footer — with:
  - Event hero + the poster image itself
  - "What to Expect" cards (from the poster)
  - Speaker section (Santosh Rebello, Global Workforce Development Head, Salesforce)
  - A **Click to Register →** button
  - "For Queries" contact grid (Sahana H, Vineet Kashyap, Bhamini V, Dishitha V)
- Pulled the site's `<style>` block out into `assets/css/theme.css` so both pages share one
  source of truth for the theme — edit colors/fonts once, both pages update.

### About the registration link

The poster's own QR code was scanned to get the actual registration link, and it's a
**Microsoft Forms** link, not Google Forms:

```
https://forms.cloud.microsoft/r/6n4XRrWVjT?origin=QRCode
```

That's what's wired into both "Click to Register →" buttons right now, since it's the real,
working destination from the poster. If you'd rather use a Google Form, swap the URL in two
places (search for `forms.cloud.microsoft` in `events/agentblazer-unveiling.html` — it appears
twice, once in the hero and once in the register section).

## Deploy to Vercel (2 minutes)

**Option A — no install, drag and drop:**
1. Go to https://vercel.com/new
2. Drag this whole folder onto the page (or "Upload" if prompted)
3. Click **Deploy** — Vercel auto-detects it as a static site
4. You'll get a live URL like `your-project.vercel.app` in under a minute

**Option B — command line:**
```bash
npm install -g vercel
cd path/to/this/folder
vercel --prod
```
Follow the prompts (log in, confirm project name) — it deploys straight from your terminal.

**Option C — GitHub (best if you'll keep updating the site):**
1. Push this folder to a new GitHub repo
2. On vercel.com → **New Project** → import that repo → Deploy
3. Every future push to `main` auto-redeploys

## QR code for the site

Once deployed you'll have a live URL. Send it back and a QR code pointing straight at your
homepage (or the event page) can be generated for you — for printing, sharing, or swapping
into future posters. A QR pointing at a URL that isn't live yet would just be a dead scan, so
this last step happens after you deploy.
