# Scramjet Proxy Browser (Local + Vercel)

## Local run (VS Code on Windows)

1. Install Node.js 20+ (LTS): https://nodejs.org/en/download
2. In PowerShell:

```powershell
cd c:\Users\alexl\Downloads\scram
npm install
npm start
```

3. Open `http://localhost:8080`

## Deploy to Vercel

This project is configured for static Vercel hosting.

### 1) Push this folder to GitHub

### 2) Import repo in Vercel
- Framework Preset: `Other`
- Build Command: auto from `vercel.json` (`npm run build`)
- Output Directory: auto from `vercel.json` (`public`)

### 3) Optional environment variable in Vercel
- Default is already wired to official Scramjet Wisp: `wss://wisp.mercurywork.shop/`
- You can override with:
  - `WISP_URL` = your own Wisp websocket URL
  - Example format: `wss://your-wisp-host.example.com/wisp/`

### 4) Deploy

## Important

Vercel does not host the required long-lived `/wisp/` websocket upgrade endpoint for this stack. This project defaults to the official Scramjet Wisp endpoint and can optionally be overridden with `WISP_URL`.

## Files

- `src/index.js` - local Fastify server (good for desktop development)
- `scripts/prepare-static.mjs` - copies proxy runtime assets to `public/`
- `scripts/generate-config.mjs` - writes `public/config.js` from env vars
- `vercel.json` - Vercel deployment/runtime headers config
- `public/index.js` - reads `window.__APP_CONFIG__.wispUrl`
- `public/config.js` - default local config
