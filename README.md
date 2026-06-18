# SeaVera AI — company site

Static marketing site for **SeaVera AI**, the parent company of **NexusHeart** (nexusheart.me) and **SureVault** (surevault.me). No build step, no framework — plain HTML/CSS/SVG, ready for free static hosting on Vercel.

## Structure

| File | Purpose |
|------|---------|
| `index.html` | Landing page: hero, two-tile product grid (links to nexusheart.me / surevault.me), mission |
| `privacy.html` | Privacy policy (served at `/privacy` via `cleanUrls`) |
| `styles.css` | All styling (responsive) |
| `favicon.svg` | Logo mark / favicon |
| `vercel.json` | Clean URLs + basic security headers |

Logo and product tiles are inline SVG so the site is fully self-contained. To use real photos later, drop images into an `assets/` folder and swap the `<svg>` blocks for `<img>`.

## Local preview

Any static server works, e.g.:

```bash
cd seavera-site
python3 -m http.server 4321
# open http://localhost:4321
```

## Deploy to Vercel (free Hobby tier)

### Option A — Vercel dashboard (no CLI)
1. Push this repo to GitHub (the `seavera-site/` folder can live inside the existing repo).
2. Go to https://vercel.com → **Add New… → Project** → import the GitHub repo.
3. In project settings set **Root Directory** to `seavera-site`.
4. **Framework Preset:** Other. **Build Command:** leave empty. **Output Directory:** leave empty (it serves the root directory as static).
5. **Deploy.** You get a free `*.vercel.app` URL with HTTPS.

### Option B — Vercel CLI
```bash
npm i -g vercel
cd seavera-site
vercel          # first run links/creates the project (accept defaults; no build)
vercel --prod   # promote to production
```

## Point seavera.ai at it
1. In the Vercel project → **Settings → Domains → Add** `seavera.ai` (and optionally `www.seavera.ai`).
2. Vercel shows the DNS records to set at your domain registrar:
   - Apex `seavera.ai` → **A** record to Vercel's IP (Vercel displays the exact value), or use Vercel nameservers.
   - `www` → **CNAME** to `cname.vercel-dns.com`.
3. Wait for DNS to propagate; Vercel auto-provisions the SSL certificate.

## Notes
- Free tier is fine for a static marketing site (generous bandwidth, free SSL, custom domain).
- Update the copyright year in `index.html` is automatic; `privacy.html` is static — edit if needed.
- Contact email referenced: `privacy@seavera.ai` (set up the mailbox/forwarding when the domain is live).
