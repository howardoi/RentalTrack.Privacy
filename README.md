# RentalTrack.Privacy

Static site that hosts the **RentTrack Privacy Policy** at
**https://privacy.rental-track.com**.

Kept separate from any future marketing/landing site (`RentalTrack.Web`) so
the legal page can be updated, redeployed, and audited on its own.

## What's here

```
index.html      The privacy policy page (the only page)
styles.css      Dark-theme styles, lifted from the RentTrack design system
README.md       This file
```

No frameworks, no build step, no dependencies. Pure HTML + CSS.

## Local preview

Open `index.html` in any browser. That's it.

Or, if you want a local web server:

```bash
# Python (any version 3.x)
python -m http.server 8000

# or Node, if you have npx
npx serve .
```

Then visit `http://localhost:8000`.

## Hosting — Cloudflare Pages

This site is deployed to **Cloudflare Pages** and served on the custom
domain `privacy.rental-track.com`.

### First-time setup

1. Push this folder to a GitHub repo (suggested: `howardoi/RentalTrack.Privacy`).
2. Cloudflare dashboard → **Workers & Pages** → **Create application** →
   **Pages** → **Connect to Git**.
3. Authorise Cloudflare to access the repo, select `RentalTrack.Privacy`.
4. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` (root)
   - **Root directory:** *(leave empty)*
5. Click **Save and Deploy**. First deploy takes ~30s.

Cloudflare gives you a default URL like `renttrack-privacy.pages.dev`.

### Bind the custom domain

1. In the Cloudflare Pages project → **Custom domains** → **Set up a
   custom domain** → enter `privacy.rental-track.com`.
2. Because `rental-track.com` already uses Cloudflare for DNS, Cloudflare
   adds the required `CNAME` record automatically.
3. SSL is provisioned automatically — usually live within 1-2 minutes.

### Updating the policy

Edit `index.html`, commit, push. Cloudflare auto-deploys on every push to
the default branch (usually `main`). Live within 30-60s.

**When you change the policy content, update both dates** at the top of
`index.html`:

```html
<strong>Effective date:</strong> <time datetime="YYYY-MM-DD">DD Mon YYYY</time>
<strong>Last updated:</strong>   <time datetime="YYYY-MM-DD">DD Mon YYYY</time>
```

If the change is **material** (new data category collected, sharing with
a new third party, etc.), notify users in the app *before* the change
takes effect, per section 11 of the policy itself.

## Notes

- **Robots:** indexable (`<meta name="robots" content="index, follow" />`)
  so the page appears in search results when users look up
  "RentTrack privacy".
- **Favicon:** referenced in `<head>` but not committed. Drop a
  `favicon.png` in this folder if you want one (use the RentTrack icon).
- **Print stylesheet** included — the page prints cleanly in black on
  white, hiding header/footer.
- **Mobile-first** breakpoints kick in at 600px.

## Contact

Owned by ThriveTech.
Policy contact + abuse reports: `howardoi8888@gmail.com`.
