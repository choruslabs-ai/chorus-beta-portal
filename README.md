# CHORUS β Control Console Portal (`v7.8.4`)

**Organization:** CHORUS Labs  
**Architect & Creator:** `inf3rno`

This GitHub Pages repository hosts the lightweight, full-viewport web wrapper for the **CHORUS β (`v7.8.4`) Control Console**, providing a clean public URL, mobile-safe viewport framing (`100dvh` + `viewport-fit=cover`), and cross-origin `postMessage` theme and session synchronization.

## Features

- **Full-Viewport Responsive Framing:** Adapts cleanly across desktop, tablet, and smartphone screens with safe-area support.
- **Cross-Origin Bridge (`CHORUS_GH_PAGES` ↔ `CHORUS_GAS_APP`):** Syncs theme preferences, query parameters, and opt-in remembered sessions without blocking direct login.
- **Strict Session Hygiene:** Clears parent storage immediately on logout or whenever **Keep me signed in** is unchecked.
- **Graceful Boot Fallback:** Displays a lightweight loading card and direct fallback link if third-party iframe cookies are restricted by the browser.

## Deployment

Update the configured Web App endpoint inside `index.html` whenever you publish a new control-plane deployment, then push to `main` to trigger GitHub Pages publishing.
