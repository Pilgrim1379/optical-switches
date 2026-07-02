# Optical Switches — Field Reference

An installable, offline-capable single-page reference for optical switches: how they
work, the key metrics (IL, ORL, crosstalk), the mirror control loop, and every test
and calibration explained. Text is rendered as HTML/SVG, so it stays sharp at any zoom.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole guide (self-contained HTML + CSS + inline SVG). |
| `manifest.webmanifest` | PWA metadata so the page can be installed to a home screen. |
| `sw.js` | Service worker — caches the app shell for offline use. |
| `icons/` | App icons (192, 512, maskable, Apple touch, favicon). |

All paths are **relative** (`./`), so this works both at a user site
(`username.github.io`) and a project sub-path (`username.github.io/repo/`).

## Host it on GitHub Pages

1. Create a repository and add these files at its **root** (keep the `icons/` folder).
2. Push to `main`.
3. Repo → **Settings → Pages** → *Build and deployment* → Source: **Deploy from a branch** →
   Branch: `main`, Folder: `/ (root)` → **Save**.
4. Wait a minute, then open the published URL (shown on the Pages settings screen).

> A service worker needs **HTTPS** — GitHub Pages serves HTTPS by default, so install
> and offline mode work once it's live. (Locally, `http://localhost` also counts as secure.)

### Install to a device
Open the live URL, then:
- **iOS Safari:** Share → *Add to Home Screen*.
- **Android/Chrome/Edge desktop:** the install icon in the address bar, or menu → *Install*.

### Test locally before pushing
```bash
cd optical-switches-site
python3 -m http.server 8080
# open http://localhost:8080
```

## Updating the content
Edit `index.html`. When you change cached assets, bump the cache name in `sw.js`
(`optical-switches-v1` → `-v2`) so returning visitors pick up the new version.
