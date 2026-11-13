# OKB Waterway Photo Desk

Chat-style page where regional offices upload waterway photos for **Oplan Kontra Baha (OKB)**.
The photos and their dates feed the public OKB Magazine.

**Live page:** https://oplankontrabaha.github.io/photosubmission/

## How it works

| Part | Where it lives | What it does |
|---|---|---|
| `index.html` | this repository (GitHub Pages) | the whole page: chat, photo review, dates, map pins, receipt |
| `Code.gs` | the Apps Script project (not in this repo) | the server: reads the OKB SSOT, checks region passwords, saves photos to Drive and rows to the upload sheet |

The page talks to the server through the Apps Script `/exec` link, saved as `API_URL` near the top of the
script in `index.html`. Every request is one `POST` with `{ "fn": "...", "args": [...] }`, and Code.gs only
answers the six functions listed in its `API_FUNCTION_NAMES`.

## Updating

- **Page changes:** edit `index.html` here and commit. GitHub Pages updates within a minute or two.
- **Server changes:** paste the new `Code.gs` into Apps Script, then
  **Deploy → Manage deployments → ✏️ Edit → Version: New version → Deploy**.
  Always edit the existing deployment: a new deployment gets a new `/exec` link, and `API_URL` would have to change too.
- **Check the server:** open the `/exec` link with `?ping=1` at the end. It should answer with `"ok": true`.
