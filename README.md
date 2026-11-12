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

## iPad camera (Chrome or Safari)

Chrome on iPad uses the same WebKit engine as Safari, so both need camera permission plus a tap on **เปิดกล้อง**.

1. Open the kiosk URL over HTTPS, enter the PIN, then tap **เปิดกล้อง** and allow the prompt.
2. If the camera does not start:

**Chrome on iPad**
- iPad Settings → Chrome → Camera → ON
- Return to the page, tap **เปิดกล้อง**, and choose Allow if a prompt appears.

**Safari on iPad**
- Settings → Safari → Camera → Ask or Allow
- Or tap the **aA** button left of the address bar → Website Settings → Camera → Allow
- Close the tab, reopen it (or refresh), then tap **เปิดกล้อง**.

Front camera is the default (kiosk facing the visitor). Use **สลับเป็นกล้องหลัง** to switch. If live scan still fails, use **ถ่ายหรือเลือกรูป QR** or **พิมพ์รหัสแขก** (the code printed under the QR, for example `V-20261113-B7MWXP`).
