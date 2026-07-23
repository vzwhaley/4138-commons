# 4138 Commons

4138commons.com — **Laravel 13 + Vue 3 + Vite + Tailwind 4**. Commercial suites
for lease at 4138 Bristol Highway, Johnson City, TN. Hosted on Cloudways
("Moon Whale Media" server `159.203.67.204`), deployed from this repo.

| | |
|---|---|
| Cloudways app id | `axhjjgqadh` |
| App root (rsync target) | `public_html` |
| **Cloudways Web Root** | `public_html/public` |
| Staging URL | https://phpstack-1647922-6572206.cloudwaysapps.com |
| Production | https://4138commons.com |
| Local dev | `https://4138commons.test` (Herd) |
| Deploy | `./deploy.sh` (must be on `main`, committed + pushed) |

## Current state
**Coming Soon page.** Route `/` → `resources/views/coming-soon.blade.php`, which
mounts the `ComingSoon.vue` component (brand logo `public/images/logo.png` with
"Coming Soon" below). No database, no forms yet. When forms are added later,
**every form gets Cloudflare Turnstile** (standing agency rule).

## Local development
```bash
composer install
npm install
npm run dev      # Vite dev server + HMR
```
The site is served by **Herd** at **https://4138commons.test** (Herd link name
`4138commons`, secured). Run `herd link 4138commons` from this folder if the link
is ever missing.

## Deploy
`./deploy.sh` builds assets locally (`npm run build`), rsyncs the app to the
Cloudways app root, runs `composer install --no-dev`, rebuilds Laravel caches,
and resets OPcache. The server needs no Node — compiled assets ship in
`public/build`. Secrets are **never** rsynced (`.env` is excluded).

### First deploy — one-time server setup
The server `.env` is not in git and is not copied by `deploy.sh`. Before the very
first cached deploy, create it on the server (over SSH `cloudways`) in
`public_html/.env`:

```
APP_NAME="4138 Commons"
APP_ENV=production
APP_KEY=            # set with: php8.4 artisan key:generate --show
APP_DEBUG=false
APP_URL=https://4138commons.com

LOG_CHANNEL=stack
LOG_LEVEL=error

DB_CONNECTION=sqlite
SESSION_DRIVER=file
CACHE_STORE=file
QUEUE_CONNECTION=sync
```

Generate the key with `php8.4 artisan key:generate --show` and paste it into `APP_KEY`.

## Go-live (Cloudways panel — shell can't do these)
1. **Application Settings → Web Root** → set to `public_html/public`.
2. **Domain Management** → add `4138commons.com` + `www.4138commons.com`, set `4138commons.com` primary.
3. **SSL Certificate** → Let's Encrypt (email: info@moonwhale.media).

DNS `@` + `www` → `159.203.67.204` at the registrar.
