# Boston Marathon Weather & Performance Simulator

## Overview
This project is an interactive web‑based simulator for the **Boston Marathon** that combines elevation, pacing, and real‑time weather modeling. It allows runners (or coaches) to:
- Set a target finish time and choose a pacing strategy.
- Visualize the course elevation profile and how temperature, humidity, and wind affect pace.
- Log race outcomes, equipment/gear details, and physiological metrics.
- Receive AI‑driven feedback and recommendations based on the logged data.
- **Automatically fetch current weather** for any location on a Leaflet map using the **Open‑Meteo API**, removing the need for manual input.

## Main Pages
- **`index.html`** – Core pacing & weather optimizer.
- **`feedback_loop.html`** – Human‑in‑the‑loop feedback portal where users submit race outcomes and view AI insights.

## Key Features
- **Dynamic Weather Modeling** – Temperature, humidity, and wind sliders (now auto‑populated from live API data).
- **Leaflet Map Integration** – Pan/zoom to any point; weather updates based on the map’s coordinates.
- **Equipment & Gear Log** – Fields for shoes, dressing, and nutrition notes.
- **AI Feedback Loop** – Stores outcomes in `localStorage`, displays deviation, risk badges, and coach recommendations.
- **Export / Import** – Export logged data as JSON for further analysis.
- **Responsive Design** – Tailwind CSS with dark mode, glassmorphism panels, and smooth micro‑animations.

## Deployment
- Hosted via **GitHub Pages** at:
  - **Site:** https://lin826.github.io/boston-marathon/
  - **Feedback Portal:** https://lin826.github.io/boston-marathon/feedback_loop.html
- Repository: https://github.com/lin826/cursor-boston
- Submodule pointer updated to include the latest changes.

## How It Works (Technical)
1. **Weather Fetching** – On page load the script calls:
   ```javascript
   https://api.open-meteo.com/v1/forecast?latitude=...&longitude=...&current_weather=true&hourly=temperature_2m,relativehumidity_2m,windspeed_10m
   ```
   The response populates hidden inputs (`temp`, `humidity`, `wind`) for the simulator.
2. **Map Interaction** – Leaflet displays a map centered on Boston. Moving the map triggers a new fetch for the selected coordinates.
3. **Simulation Logic** – Uses the temperature, humidity, wind, and gradient data to compute a pacing multiplier, safety risk, and hydration recommendations.
4. **Feedback Storage** – Outcomes are saved in `localStorage` as `marathon_outcomes` and rendered in a table with AI‑generated insights.

## Future Enhancements (Ideas)
- Persist map location across sessions.
- Fetch mile‑by‑mile temperature forecasts to create a true temperature **time‑series**.
- Integrate a backend (e.g., Netlify Functions) for permanent data storage and model retraining.
- Add a downloadable PDF report of the race analysis.

---
*Generated on 2026‑05‑26 by Antigravity AI coding assistant.*
