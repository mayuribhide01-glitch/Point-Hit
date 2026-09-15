# BLOCKFALL — AR Sky Defense

A single-file, self-contained AR mobile web game. No build step, no server-side code, no external assets besides two CDN-hosted libraries (Three.js from cdnjs, Google Fonts).

## Deploy on GitHub Pages
1. Create a new GitHub repo (or use an existing one).
2. Add `index.html` to the repo root (this is the same file as `blockfall.html` — either works, `index.html` is just named for Pages' default entry point).
3. Push to GitHub.
4. In the repo, go to **Settings → Pages**, set **Source** to your default branch and root folder (`/`), save.
5. GitHub gives you a URL like `https://<username>.github.io/<repo>/` — open it on an iPhone in Safari.

## Important: HTTPS is required
Camera access (`getUserMedia`) and motion access (`DeviceOrientationEvent.requestPermission`) only work on a secure origin. GitHub Pages serves over HTTPS automatically, so this is already handled — just don't try to open the raw file with `file://` locally, since camera/motion won't be granted that way. Serve it over `http://localhost` or any HTTPS host for local testing instead.

## Files
- `index.html` / `blockfall.html` — the entire game (HTML + CSS + JS in one file)

## Known platform limitation
iOS Safari does not implement the Vibration API (`navigator.vibrate`), so true haptic feedback isn't available in a browser context on iPhone — this is a platform restriction, not a bug in the code. The game compensates with screen-flash, camera-shake, and layered sound cues on impact events. Real Taptic Engine haptics on iPhone would require wrapping this as a native app (e.g. via Capacitor).
