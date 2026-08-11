# Mobilise Tap — hackathon web app

A mobile-first web app for the "make homelessness impossible to walk past" challenge.
Someone scans a QR on a rough sleeper's charity-issued card → the app opens → they
choose **Funds · Food · Gig · Gear** → a mock, verified, closed-loop confirmation →
a "see what happened next" outcome text.

Built to match Mobilise's brand and Direct Giving model (funds route through a charity
partner toward housing; the giver gets told what their help did).

> All payments are **simulated** — the ribbon says DEMO. No money moves. Perfect for
> pitching; you can wire up Stripe later.

## Files
- `index.html` — the whole app (single file, no build step)
- `qr.html` — paste your live URL, generate + download a QR to print
- `README.md` — this file

## Run it locally
Just open `index.html` in a browser, or serve the folder:
```
npx serve .
```

## Deploy free on Vercel (2 minutes)

### Option A — drag & drop (easiest)
1. Go to https://vercel.com and sign up (free).
2. Click **Add New… → Project → Deploy** (or use https://vercel.com/new).
3. When it asks for a framework, choose **Other** — there is no build step.
4. Drag this whole folder in (or connect the GitHub repo below). Deploy.
5. Copy your live URL, e.g. `https://mobilise-tap.vercel.app`.

### Option B — GitHub + Vercel (best for editing later)
1. Create a new GitHub repo and upload these files.
2. In Vercel: **Add New → Project → Import** that repo.
3. Framework preset: **Other**. Leave build/output blank. Deploy.

### Option C — Vercel CLI
```
npm i -g vercel
vercel        # from inside this folder, follow the prompts
vercel --prod
```

## Make the QR
1. After deploying, open `https://your-app.vercel.app/qr.html`.
2. Your URL is pre-filled — click **Generate QR**, then **Download PNG**.
3. Print it on David's card / your stand. Scanning it opens the app.

## Customise (quick wins)
- **The person:** edit the profile block in `index.html` (name, story, goal, `%` in
  `.bar > i { width:62% }`, the "$210 raised / 62%" line).
- **Charity partner name:** find & replace `Launch Housing`.
- **Amounts / options:** edit the `CONFIG` object near the bottom of `index.html`.
- **Colours:** the `:root` CSS variables at the top (already Mobilise blue→green).

## Wire up real payments later (optional)
Swap the `pay()` function for a Stripe Checkout redirect (test mode uses fake cards):
create a Payment Link in the Stripe dashboard and point the confirm button at it, or
add a tiny Vercel serverless function under `/api`. Ask and I'll set it up.
