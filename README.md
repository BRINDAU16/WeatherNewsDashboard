# WeatherNewsDashboard
# 🌤️ Horizon Dashboard

A dark, sleek Weather & News dashboard built with pure HTML, CSS, and JavaScript. No frameworks, no dependencies — just one file that works in any browser.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green?style=flat)

---

## 🖥️ Live Demo

> Hosted on GitHub Pages — [your-username.github.io/horizon-dashboard](https://your-username.github.io/horizon-dashboard)

---

## ✨ Features

- **📍 Auto location detection** — uses the browser's built-in GPS to detect your location on load
- **🌡️ Current weather** — temperature, feels like, humidity, wind speed & pressure
- **📅 5-day forecast** — daily high/low with weather icons
- **💨 Air quality index** — animated ring with PM2.5, PM10, NO₂ and O₃ readings
- **☀️ UV index** — colour-coded bar with sun protection advice
- **🕐 Live clock** — real-time clock and date in your local timezone
- **📰 Top news headlines** — filterable by General, Technology, and Science
- **🔍 City search** — manually search any city worldwide
- **🔄 Auto-refresh** — data refreshes every 10 minutes automatically
- **📱 Fully responsive** — works on desktop, tablet, and mobile

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/your-username/horizon-dashboard.git
cd horizon-dashboard
```

### 2. Get your free API keys

| API | Purpose | Free tier |
|-----|---------|-----------|
| [OpenWeatherMap](https://openweathermap.org/api) | Weather, AQI, forecast | 1,000 calls/day |
| [NewsAPI](https://newsapi.org) | News headlines | 100 requests/day |

Sign up on each site and copy your API key from the dashboard.

### 3. Add your keys to the file

Open `dashboard.html` and find these two lines near the top of the `<script>` section:

```javascript
const OWM_KEY  = 'YOUR_OWM_KEY';
const NEWS_KEY = 'YOUR_NEWS_KEY';
```

Replace the placeholders with your actual keys.

### 4. Run locally

NewsAPI's free tier requires a server (not a plain file). Start a local server with Python:

```bash
# Python 3
python -m http.server 8080
```

Then open [http://localhost:8080/dashboard.html](http://localhost:8080/dashboard.html) in your browser.

---

## 🌍 Location Detection

When the page loads, the browser will ask:

> *"Allow this page to know your location?"*

- **Allow** → weather and AQI load for your exact GPS coordinates automatically
- **Block** → falls back to London by default; you can still search any city manually

> **Note:** Geolocation only works over `https://` or `localhost`. It works perfectly on GitHub Pages.

---

## 📁 Project Structure

```
horizon-dashboard/
├── dashboard.html    # The entire app — HTML, CSS, and JS in one file
└── README.md         # You're reading this!
```

---

## 🧠 How It Works

### Geolocation
```javascript
navigator.geolocation.getCurrentPosition(
  pos => fetchWeatherByCoords(pos.coords.latitude, pos.coords.longitude),
  ()  => fetchWeather('London') // fallback if denied
);
```

### Weather API call
```javascript
fetch(`https://api.openweathermap.org/data/2.5/weather
       ?lat=${lat}&lon=${lon}&appid=${OWM_KEY}&units=metric`)
```

### Live clock
```javascript
// new Date() always reads the device's local timezone automatically
const now = new Date();
document.getElementById('clock-time').textContent =
  `${now.getHours()}:${now.getMinutes()}:${now.getSeconds()}`;
```

### Auto-refresh
```javascript
// Refreshes all data every 10 minutes
setInterval(() => {
  fetchWeatherByCoords(lat, lon);
  fetchNews(category);
}, 600000);
```

---

## 🎨 Customisation

All colours are CSS variables at the top of the `<style>` block:

```css
:root {
  --bg:      #080c10;   /* page background  */
  --accent:  #4fc3f7;   /* highlight colour */
  --card:    #111820;   /* card background  */
  --text:    #e8edf2;   /* main text        */
}
```

Change `--accent` to any colour to instantly retheme the whole dashboard.

---

## 💡 Ideas to Extend

- [ ] Add an hourly forecast chart using Chart.js
- [ ] Add a dark/light mode toggle
- [ ] Show a map of the detected location using Leaflet.js
- [ ] Add severe weather alerts
- [ ] Save preferred city to `localStorage`
- [ ] Add more news categories (sports, health, business)

---

## 📚 What I Learned

This project covers key intermediate web development concepts:

- Calling **REST APIs** with `fetch()` and handling JSON responses
- Using the **Geolocation API** to get the user's GPS coordinates
- **Async/await** and error handling with `try/catch`
- Dynamic **DOM manipulation** — building UI from live data
- **CSS Grid** for a responsive multi-column dashboard layout
- CSS variables, animations, and a cohesive dark theme
- Auto-refresh patterns with `setInterval`

---

## 🔑 API Reference

| Endpoint | Used for |
|----------|---------|
| `api.openweathermap.org/data/2.5/weather` | Current weather by city or coords |
| `api.openweathermap.org/data/2.5/forecast` | 5-day forecast + UV index |
| `api.openweathermap.org/data/2.5/air_pollution` | Air quality index |
| `newsapi.org/v2/top-headlines` | News headlines by category |

---

