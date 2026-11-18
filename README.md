# CHORUS β Control Console Portal (`v7.8.4`)

**Organization:** CHORUS Labs  
**Architect & Creator:** `inf3rno`

This GitHub Pages repository hosts the lightweight, full-viewport web wrapper for the **CHORUS β (`v7.8.4`) Google Apps Script Control Plane**, providing a clean URL, mobile-safe viewport framing (`100dvh` + `viewport-fit=cover`), and cross-origin `postMessage` theme and session synchronization.

---

## Live Control Plane Endpoint

- **Google Apps Script Web App (`v7.8.4`):**  
  `https://script.google.com/macros/s/AKfycbzZhYio-ZgGYBYWqddBxq_TsLtjpax9xJJg8cFm9tvHBRu6i0zK6EQuxqSemD8NFl9A/exec`

---

## Architecture & Bridge Protocol

`index.html` embeds the Google Apps Script Web App in a full-viewport `<iframe>` and communicates with `Scripts_TelemetryAndPortal.html` over the verified `CHORUS_GH_PAGES` ↔ `CHORUS_GAS_APP` `postMessage` bridge:

| Direction | Message Type | Purpose |
|-----------|--------------|---------|
| GAS → Portal | `CHORUS_APP_LOADED` | Signals iframe DOM boot complete; dismisses splash screen and triggers theme/session check. |
| Portal → GAS | `CHORUS_RESTORE_SESSION` | Forwards saved theme and (only if **Remember Me** is enabled inside the console) remembered session metadata. |
| GAS → Portal | `CHORUS_APP_READY` | Confirms authenticated workspace or centered login portal is interactive. |
| GAS → Portal | `CHORUS_SESSION_SAVED` | Syncs remembered session token/guild when **Keep me signed in (30 days)** is checked; clears parent storage when unchecked. |
| GAS → Portal | `CHORUS_SESSION_CLEARED` | Purges parent `localStorage` immediately on logout or unremembered visit. |

---

## Updating the Deployment URL

When you create a new Google Apps Script Web App deployment, update `GAS_WEBAPP_URL` and the `<iframe src>` / fallback link in `index.html`, then push to `main` (GitHub Pages auto-publishes within ~1 minute).

Pair this portal with:
- **Apps Script Control Plane:** `apps_script_v7.8.4_Production_Verified.zip`
- **Discord Bot Execution Plane (Railway):** `CHORUS-BOT_v7.8.4_Railway_Verified.zip`
