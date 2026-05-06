# Zahara Schaefer Personal Page - Cloudflare Worker

Static site clone of the PHP personal-page running as a Cloudflare Worker.

## URLs

- **Worker:** https://zahara-personal-page.layereightsolutions.workers.dev
- **Domain:** https://zaharaschaefer.com (pointed via CF DNS)
- **GitHub:** https://github.com/l8-runa/zahara-personal-page

## Cloudflare Credentials

Stored in `~/.bashrc`:
```bash
export CLOUDFLARE_API_TOKEN=<your-token-here>
export CLOUDFLARE_ACCOUNT_ID=e7a737dd013468f9078050ae69ac423d
```

## Deploy

```bash
cd ~/.hermes/runa-worker
npx wrangler deploy
```

## Development

```bash
# Start local PHP server for rendering
cd ~/projects/personal-page/www
php -S localhost:8888

# Render pages (prod mode)
curl -s -H "Host: zaharaschaefer.com" http://localhost:8888/

# Deploy
npx wrangler deploy
```

## Architecture

- **24 pages** embedded directly in `src/index.js` (PAGES object)
- **Static assets** in `public/assets/` served via Workers Assets
- **Case-insensitive routing** - /CV, /N8N, etc. all work
- **Custom 404** page included

## Pages (24 total)

| Route | Page |
|-------|------|
| `/`, `/home` | home |
| `/about` | about |
| `/services` | services |
| `/contact-me`, `/contact` | contact |
| `/cv` | cv |
| `/pronouns` | pronouns |
| `/login` | login |
| `/referral-programs`, `/referral` | referral |
| `/self-service` | self-service |
| `/n8n` | n8n |
| `/zapier-to-n8n` | zapier-to-n8n |
| `/make-to-n8n` | make-to-n8n |
| `/switch-to-n8n` | switch-to-n8n |
| `/switch-to-mautic` | switch-to-mautic |
| `/proxmox` | proxmox |
| `/proxmox-virtualization` | proxmox-virtualization |
| `/3-2-1-1-0-backup-strategy` | 3-2-1-1-0-backup-strategy |
| `/activecampaign` | activecampaign |
| `/clickfunnels` | clickfunnels |
| `/gohighlevel` | gohighlevel |
| `/keap` | keap |
| `/oncehub` | oncehub |
| `/posthog` | posthog |
| `/kb-support` | kb-support |

## Known Issues Fixed

1. **"Firstname Lastname"** - Fixed by updating `site-name.php` to always return "Zahara Schaefer"
2. **Case-insensitive routing** - Added lowercase normalization
3. **White-on-white text** - Fixed gradient card text colors in pronouns.css
4. **404 page** - Added custom purple-themed 404

## Tech Stack

- Cloudflare Workers + Workers Assets
- Wrangler v4
- Vanilla JS (no build step needed for worker)

## PostHog

- Token: `phc_UKB0NrUR2lv55xa0u74VPOLaBFp6DTybsomwEYUU7AF`
- API Host: `https://us.i.posthog.com`