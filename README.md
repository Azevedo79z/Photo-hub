# PHOTO HUB — Phase 1 foundation

Futuristic, standalone public photography gallery. Google Drive is the planned source of originals; public visitors will only see items explicitly published by an administrator.

## Stack
- Astro + React
- Tailwind CSS v4
- Cloudflare Workers (standalone deployment)
- Google Drive API v3 integration planned for Phase 2

## Local development
Requirements: Node.js 20.19+ or 22.12+ and npm.

```bash
npm install
npm run dev
```

Open the local URL printed by Astro.

## Build and deploy
```bash
npm run build
npx wrangler login
npm run deploy
```

Before deploying, confirm the Cloudflare account and Worker name. Add production secrets through Cloudflare/Wrangler secrets, never in source files.

## Google Drive source
Configured folder ID: `1Pkzi6XII5LdPqxcudX1dY5-mL599Grw4`

The folder has not yet been inspected or connected by this starter. Phase 2 will add Google OAuth, Drive API access, folder traversal, and a server-side media delivery/cache layer.

## Security model
- Public routes expose only published album/photo metadata.
- Google OAuth tokens and client secrets remain server-side.
- No public write access to the source Drive.
- Admin actions require an allowlisted Google account.
- Deletion will require confirmation; archive/unpublish is preferred.
- Do not place secrets in `PUBLIC_*` variables or commit `.env`.

## Planned routes
- `/` — public landing page
- `/galeria` — published albums
- `/album/[slug]` — public album
- `/admin` — protected administration (Phase 4)
- `/api/*` — server-side endpoints (added as needed)

## Phase 1 scope
This starter provides the independent project shell, visual system, responsive landing page, and Cloudflare Worker configuration. Drive integration, live photo data, admin login, and production deployment are deliberately not claimed as complete.
