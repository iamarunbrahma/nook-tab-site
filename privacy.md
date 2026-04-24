# Privacy: Nook Tab

_Last updated: 24 April 2026_

I built Nook Tab because I wanted a quiet new tab for my own browser, not a dashboard that phones home about every click. So the privacy story is short:

> **Nothing you do in Nook Tab is sent to me, tracked, or sold to anyone.**

---

## What stays on your device

The extension keeps a handful of things in your browser's local storage (a file Chrome manages on your computer). It never leaves:

- Your display name, if you set one
- Your preferences: °C/°F, 12h/24h clock, Pomodoro durations
- The running state of the Pomodoro timer, so it stays in sync across your open tabs (still only on your device)
- The text, colour, and position of your sticky notes
- Your last-played ambient track and the volume you left it at
- A cached weather response and your coarse location (both refreshed rarely)
- Which wallpaper is today's (just an index into the catalog)

Uninstall the extension and all of the above disappears with it.

---

## What actually leaves your device

Nook Tab stays silent until a feature needs the internet. There are five moments that do.

### 1. "Where am I, roughly?"

Once a week at most, the extension pings [GeoJS](https://www.geojs.io/) based on your public IP so the weather pill can name your city and country, without Chrome poking you for the geolocation permission. Nothing else is sent in that request.

### 2. "What's the weather?"

Up to once every 30 minutes, the coordinates from step 1 go to [Open-Meteo](https://open-meteo.com) for a current temperature and a weather code. Open-Meteo needs no account and sets no cookies.

### 3. Voice search, only when you press the mic

Chrome's built-in Web Speech API streams microphone audio to Google for transcription and hands Nook Tab the text back. Nook Tab never touches the audio itself. Don't press the mic and no audio is ever captured. On browsers without Web Speech, the mic button simply doesn't appear.

### 4. Your actual search

Hitting Enter with a search term hands the query to Chrome's Search API, which loads results using whatever search engine you've set as default in Chrome (Google, DuckDuckGo, or anything else you've chosen). Nook Tab doesn't pick a provider for you and nothing detours through me. If what you typed looks like a URL, the tab navigates there directly.

### 5. The wallpaper and the ambient tracks

To keep the extension small, the wallpaper images and the ambient audio loops are not bundled inside the extension. They live in a public GitHub repo I own and are served through [jsDelivr](https://www.jsdelivr.com), a free open-source CDN run on top of Cloudflare. The first time you see a particular wallpaper or play a particular track, your browser fetches that one file from `cdn.jsdelivr.net`. Your browser then caches it, so later visits load instantly and work offline. The request carries no cookies, no account, no identifier I add. jsDelivr's CDN sees a normal HTTP request for the file from your IP, the same as opening any image on the open web.

---

## Things Nook Tab deliberately doesn't do

No analytics. No crash reporting. No "anonymous usage stats." No account. No cross-device sync. No ads, affiliate links, remarketing pixels, or fingerprinting. If someone ever offers to buy this extension and asks to change that, I'll say no.

---

## The permissions, explained

The `manifest.json` asks for two things and nothing else:

- `"storage"`, so your settings survive a browser restart
- `"search"`, so the search bar hands your query to Chrome's own Search API and uses whatever default engine you already have configured
- `"host_permissions"` for `api.open-meteo.com`, `get.geojs.io`, and `cdn.jsdelivr.net`, the only three domains the extension is allowed to reach

Microphone access isn't in the manifest. Chrome handles that on the fly the first time you press the mic.

---

## Kids

Nook Tab doesn't ask for anyone's age. Since no personal data is collected in the first place, there's nothing particular to add here. This line exists only because some policy templates expect one on under-13 users.

---

## When this changes

Any change to what data leaves your device will ship in the same commit that bumps the version at the top of this file. The freshest copy always lives at the URL in the Chrome Web Store listing.

---

## Questions or bugs

Open an issue on the public repo for this site: <https://github.com/iamarunbrahma/nook-tab-site/issues>. I see everything that gets filed there.
