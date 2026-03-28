# Horizon Dashboard

A self-contained weather and news dashboard built with vanilla HTML, CSS, and JavaScript. No build tools, no frameworks — just open the file.

---

## What it shows

- **Live clock** — local time and date, auto-updating every second
- **Current weather** — temperature, description, feels like, humidity, wind, pressure
- **Air quality** — AQI index (1–5) with PM2.5, PM10, NO₂, O₃ readings
- **UV index** — value, severity label, and sun protection tip
- **5-day forecast** — daily high/low with weather icons
- **Top headlines** — filterable by General, Tech, or Science

---

## Quick start

1. Get two free API keys (takes ~2 minutes):
   - **OpenWeatherMap**: https://openweathermap.org/api → sign up → *API keys* tab
   - **GNews**: https://gnews.io → sign up → copy your key from the dashboard

2. Open `index.html` in a text editor and find this block near the bottom:

```js
const OWM_KEY   = 'YOUR_OWM_KEY';
const GNEWS_KEY = 'YOUR_NEWS_KEY';
```

3. Replace both placeholder strings with your actual keys:

```js
const OWM_KEY   = 'abc123...';   // your OpenWeatherMap key
const GNEWS_KEY = 'xyz789...';   // your GNews key
```

4. Save the file, then open it in any modern browser — no server needed.

---

## Without API keys (demo mode)

If you skip step 2–3, the dashboard still works. It shows static sample data for London so you can preview the layout. A yellow "⚡ Demo mode" label appears in each panel.

---

## Changing the default city

The dashboard tries to use your browser's GPS on load. If you deny that permission, it falls back to **London**.

To change the fallback city, find this line near the top of the `<script>` block:

```js
let currentCity = 'Bangalore';
```

Change `'Bangalore'` to any city name supported by OpenWeatherMap (e.g. `'Mumbai'`, `'New York'`, `'Tokyo'`).

You can also search any city at runtime using the input in the top-right corner.

---

## File structure

```
index.html   ← the entire app — HTML, CSS, and JS in one file
README.md    ← this file
```
