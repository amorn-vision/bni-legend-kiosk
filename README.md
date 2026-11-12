# BNI Legend — Static Kiosk

Personal project of Boss Joe (not Amorn Vision company work).

Single-page kiosk for the registration table: live front camera, welcome overlay, chime + Thai speech. It talks to the **public** Apps Script web app with a PIN that the admin sets in the staff backend.

Do **not** deploy this to the company Vercel team `amorn-vision-erp` (account `adminamornvision-1839`). Use a personal account (for example isukasame@gmail.com).

## Deploy (after signing in on this computer)

From this folder, any HTTPS static host is fine. Examples:

```bash
# Vercel — personal account only, new project
npx vercel --yes --name bni-legend-kiosk --prod

# Netlify
npx netlify deploy --prod --dir .

# Cloudflare Pages
npx wrangler pages deploy . --project-name bni-legend-kiosk

# GitHub Pages (personal repo)
# put index.html at the repo root and enable Pages
```

The site must be served over **HTTPS** or the browser will not open the camera.

## After you have a URL

1. Open the staff admin (`?page=admin`) as isukasame.
2. Tab **ทีมงาน** → **ตั้งค่าคีออสก์**: set a 4–12 character PIN, paste the HTTPS kiosk URL, save both.
3. Open that URL on the tablet, enter the same PIN, allow the camera, then tap **เริ่มโหมดคีออสก์**.

Until a PIN is saved, the API refuses every request.

API base URL is set once at the top of `index.html` (`API_BASE`) and points at the TEST public deployment.
