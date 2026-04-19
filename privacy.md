# Privacy Policy — Nook Tab

_Last updated: 2026-04-18_

Nook Tab is built with privacy as a first-class concern. There is no account, no analytics, no tracking, and no data of yours is sent to a server operated by the extension's developer.

This policy explains exactly what data stays on your device, what data leaves your device (and to whom), and why.

---

## 1. Data stored locally on your device

The extension persists the following in `chrome.storage.local` — which is sandboxed to your browser profile and never uploaded anywhere by the extension:

- Your display name (if you choose to enter one)
- Unit preference (°C / °F)
- Clock format preference (24h / 12h)
- Search-engine preference (Google / Bing / DuckDuckGo)
- Pomodoro-timer durations and the current running-state snapshot
- Sticky-note contents and positions
- Last-played ambient-audio track and volume
- The cached weather response and your cached coarse location
- Which wallpaper is selected for the current day (an index into the bundled image set)

This data is only accessible to Nook Tab on your device. Uninstalling the extension removes it.

## 2. Data sent to third parties

Nook Tab makes four kinds of optional outbound network requests. You can disable each by not using the corresponding feature. Nothing is sent at install time.

### 2.1 IP-based geolocation (ipapi.co)

**What is sent:** a standard HTTP GET request to `https://ipapi.co/json/`. The request carries your public IP address as the request origin (unavoidable for any HTTP call). No other data is attached.

**What is received:** your approximate city, country, latitude, and longitude.

**Why:** to power the weather pill at the top-right without the friction of a browser geolocation permission prompt.

**Frequency:** at most once every 7 days (cached locally).

**Provider's policy:** <https://ipapi.co/privacy/>

### 2.2 Weather forecast (Open-Meteo)

**What is sent:** a standard HTTP GET request to `https://api.open-meteo.com/v1/forecast` with your approximate latitude and longitude (from step 2.1) as query parameters.

**What is received:** the current temperature and a weather-condition code.

**Why:** to display the weather on your new tab.

**Frequency:** at most once every 30 minutes (cached locally).

**Provider's policy:** Open-Meteo does not require registration, does not set cookies, and states it does not track users. <https://open-meteo.com/en/terms>

### 2.3 Voice search (Chrome Web Speech API)

**What is sent:** when (and only when) you press the microphone button in the search bar, Chrome streams audio from your microphone to Google's speech-recognition service in order to transcribe it. This is Chrome's built-in implementation; Nook Tab does not capture, store, or transmit the audio itself — it only receives the resulting text transcript back from Chrome.

**What is received:** a text transcript that Nook Tab uses as your search query.

**Why:** to let you search hands-free.

**Frequency:** only while the microphone button is actively listening.

**Provider's policy:** Google's privacy policy governs any data Chrome sends to its speech service. <https://policies.google.com/privacy>

If you never press the microphone button, no audio is ever captured or transmitted. The microphone icon is hidden on browsers that do not support the Web Speech API.

### 2.4 Search redirection

When you submit a search, the page you typed or a search-results page is loaded in the same tab. This is a normal page navigation — no data is sent to Nook Tab's developer. The query goes directly to Google, Bing, or DuckDuckGo (whichever you selected). Their respective privacy policies apply.

## 3. Data Nook Tab does *not* do

- No analytics, metrics, or telemetry — the extension makes no request that contains usage information.
- No account, no sign-in, no sync across devices.
- No tracking scripts, no third-party fonts, no beacons.
- No ads, no affiliate links.
- No sale or sharing of any data whatsoever.
- No persistent cookies set by the extension.

## 4. Permissions explained

The extension requests these two kinds of permissions in `manifest.json`:

- **`storage`** — required to save your preferences and state locally (see section 1).
- **`host_permissions` for `api.open-meteo.com` and `ipapi.co`** — required to call the two weather-related APIs described above.

No other permissions are requested. In particular, the extension does not request access to tabs, browsing history, bookmarks, cookies, clipboard, downloads, or any other site's content.

Microphone access is governed by Chrome itself and is requested on demand by Chrome's Web Speech API — not by Nook Tab — only when you click the microphone button.

## 5. Children's privacy

Nook Tab does not knowingly collect data from children under 13. Since the extension does not collect personal data at all, this section is precautionary.

## 6. Changes to this policy

If a future version of the extension changes what is sent to third parties, this file will be updated in the same commit that makes the change, and the version number at the top of this file will be bumped.

## 7. Contact

Issues and questions: <https://github.com/iamarunbrahma/nook-tab/issues>
