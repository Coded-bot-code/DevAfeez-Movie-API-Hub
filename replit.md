# RUNFLIX Movies API

A high-throughput movie and series metadata API (v3) built with Node.js/Express for local development and Cloudflare Workers for production deployment.

## Stack

- **Runtime:** Node.js (ES modules)
- **Local server:** Express (`local-server.js`) — port 5000
- **Production:** Cloudflare Worker (`worker.js`) via Wrangler
- **Frontend:** Static HTML pages (index, docs, admin, changelog, try, stats)

## How to run

The dev server starts automatically via the **Start application** workflow:

```
PORT=5000 node local-server.js
```

## Pages

| Path | Description |
|------|-------------|
| `/` | Landing page |
| `/docs` | API documentation |
| `/try` | Interactive API explorer (free, no key) |
| `/request-key` | API key request form |
| `/admin` | Admin panel |
| `/changelog` | Changelog |
| `/debug/logs-view` | Live request log viewer |

## API endpoints (v3)

All endpoints accept an `Authorization: Bearer <key>` header (or use `/try` for 50 free calls/day).

- `GET /api/v3/homepage` — Homepage sections
- `GET /api/v3/trending` — Trending titles
- `GET /api/v3/search/:query` — Keyword search
- `GET /api/v3/info/:id` — Title info
- `GET /api/v3/sources/:id` — Stream/download links
- `GET /api/v3/captions/:sid/:strmId` — Subtitle tracks
- `GET /api/v3/anime` — Anime catalog
- `GET /api/v3/schedule` — Anime airing schedule
- `GET /api/v3/filter` — Filter by platform/genre/region

## Environment variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PORT` | 3400 | HTTP port (set to 5000 for Replit) |
| `SMTP_HOST` | mail.runflix.name.ng | SMTP server |
| `SMTP_PORT` | 587 | SMTP port |
| `SMTP_USER` | support@runflix.name.ng | SMTP username |
| `SMTP_PASS` | *(empty)* | SMTP password — set as a secret |
| `PROXY_LIST` | *(none)* | Comma-separated proxy URLs for outbound requests |
| `CF_WORKER_URL` | *(none)* | Cloudflare Worker relay URL |

## Deployment (Cloudflare Workers)

```
npx wrangler deploy
```

Requires a Cloudflare account with the KV namespace configured in `wrangler.toml`.

## User preferences

- Run on port 5000 for Replit webview compatibility.
