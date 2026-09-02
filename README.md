# tradecraft-fair-websites

This is the TradeCraft sales one-pager — a single static HTML page, not an Eleventy
site like the county demos. There is nothing to build. Cloudflare just needs to serve
the one file in `public/index.html`.

## Deploying (Cloudflare Worker, Git-connected)

1. Push this folder to a new **private** GitHub repo named `tradecraft-fair-websites`
   (or whatever you like — the repo name doesn't need to match the live URL).
2. In Cloudflare: Workers & Pages → Create → Workers → connect to Git → pick this repo.
3. Build settings:
   - **Build command:** leave blank (there is nothing to build)
   - **Deploy command:** `npx wrangler deploy`
   - **Root directory:** `/`
4. Deploy. The live URL will be `https://tradecraft-fair-websites.<your-account-subdomain>.workers.dev`
   — the name comes from `wrangler.toml`'s `name` field, not the Cloudflare project's
   display name.
5. Confirm auto-deploy on push is turned on (Settings → Builds & deployments) — same
   gotcha as the county sites, it can default to off.

## Updating the page later

Edit `public/index.html` directly (in GitHub's browser editor is fine — it's plain
HTML/CSS, no dotfile tricks needed here) and commit. If auto-deploy is on, Cloudflare
rebuilds automatically within a minute or two.
