<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Joe's Garden Planner — Lawrence, KS</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --soil: #2C1810;
  --soil-light: #3D2317;
  --leaf: #4A7C59;
  --leaf-light: #6B9F7D;
  --leaf-dark: #2D5A3A;
  --sun: #E8A832;
  --sun-light: #F5C563;
  --tomato: #C0392B;
  --pepper: #E74C3C;
  --herb: #27AE60;
  --squash: #F39C12;
  --cool: #2980B9;
  --warm: #D35400;
  --cream: #FAF3E8;
  --cream-dark: #EDE1CC;
  --text: #1A1208;
  --text-light: #5C4A2E;
  --card-bg: rgba(255,255,255,0.92);
  --frost-blue: #5DADE2;
  --alert-red: #E74C3C;
  --alert-yellow: #F39C12;
  --alert-green: #27AE60;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Outfit', sans-serif;
  background: var(--cream);
  color: var(--text);
  overflow-x: hidden;
}

/* ====== HERO ====== */
.hero {
  background: linear-gradient(135deg, var(--soil) 0%, var(--soil-light) 40%, var(--leaf-dark) 100%);
  padding: 3rem 2rem 2.5rem;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(232,168,50,0.15) 0%, transparent 70%);
  border-radius: 50%;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.hero h1 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2rem, 5vw, 3.2rem);
  color: var(--cream);
  letter-spacing: -0.5px;
  line-height: 1.15;
}

.hero h1 span { color: var(--sun); }

.hero-meta {
  display: flex;
  gap: 1.5rem;
  margin-top: 1rem;
  flex-wrap: wrap;
}

.hero-meta .badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  background: rgba(255,255,255,0.1);
  border: 1px solid rgba(255,255,255,0.15);
  padding: 0.35rem 0.8rem;
  border-radius: 100px;
  color: var(--cream-dark);
  font-size: 0.85rem;
  font-weight: 400;
  backdrop-filter: blur(4px);
}

/* ====== WEATHER BAR ====== */
.weather-bar {
  background: var(--card-bg);
  border-bottom: 1px solid var(--cream-dark);
  padding: 1rem 2rem;
  backdrop-filter: blur(10px);
  position: sticky;
  top: 0;
  z-index: 100;
}

.weather-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.weather-current {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.weather-temp {
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--text);
  line-height: 1;
}

.weather-desc {
  font-size: 0.8rem;
  color: var(--text-light);
  line-height: 1.3;
}

.weather-forecast {
  display: flex;
  gap: 0.75rem;
  margin-left: auto;
}

.forecast-day {
  text-align: center;
  padding: 0.3rem 0.6rem;
  border-radius: 8px;
  min-width: 56px;
}

.forecast-day .day-name {
  font-size: 0.65rem;
  color: var(--text-light);
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 0.5px;
}

.forecast-day .day-icon { font-size: 1.2rem; margin: 0.15rem 0; }
.forecast-day .day-temps {
  font-size: 0.7rem;
  color: var(--text);
  font-weight: 500;
}

.frost-alert {
  width: 100%;
  padding: 0.6rem 1rem;
  border-radius: 8px;
  font-size: 0.82rem;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  animation: pulse-alert 2s infinite;
}

.frost-alert.danger { background: rgba(231,76,60,0.12); color: var(--alert-red); border: 1px solid rgba(231,76,60,0.25); }
.frost-alert.warning { background: rgba(243,156,18,0.12); color: var(--alert-yellow); border: 1px solid rgba(243,156,18,0.25); }
.frost-alert.safe { background: rgba(39,174,96,0.12); color: var(--alert-green); border: 1px solid rgba(39,174,96,0.25); }

@keyframes pulse-alert {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.85; }
}

/* ====== NAV TABS ====== */
.nav-tabs {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1.25rem 2rem 0;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.tab-btn {
  padding: 0.55rem 1.1rem;
  border: 1px solid var(--cream-dark);
  border-bottom: none;
  border-radius: 10px 10px 0 0;
  background: transparent;
  font-family: 'Outfit', sans-serif;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--text-light);
  cursor: pointer;
  transition: all 0.2s;
}

.tab-btn:hover { background: rgba(74,124,89,0.08); }
.tab-btn.active {
  background: var(--card-bg);
  color: var(--leaf-dark);
  border-color: var(--leaf-light);
  font-weight: 600;
}

/* ====== SECTIONS ====== */
.section { display: none; max-width: 1200px; margin: 0 auto; padding: 0 2rem 3rem; }
.section.active { display: block; }

.section-card {
  background: var(--card-bg);
  border-radius: 0 12px 12px 12px;
  border: 1px solid var(--cream-dark);
  padding: 2rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 2px 12px rgba(0,0,0,0.04);
}

h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 1.6rem;
  color: var(--soil);
  margin-bottom: 1rem;
}

h3 {
  font-family: 'DM Serif Display', serif;
  font-size: 1.15rem;
  color: var(--soil-light);
  margin-bottom: 0.75rem;
}

/* ====== SEED TRAYS ====== */
.tray-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
  gap: 1.25rem;
}

.tray {
  background: #D2B48C;
  border-radius: 12px;
  padding: 1rem;
  border: 3px solid #A0826D;
  box-shadow: inset 0 2px 8px rgba(0,0,0,0.15), 0 4px 12px rgba(0,0,0,0.1);
  position: relative;
}

.tray-label {
  position: absolute;
  top: -10px;
  left: 12px;
  background: var(--soil);
  color: var(--cream);
  padding: 0.2rem 0.7rem;
  border-radius: 6px;
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.tray-pods {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 6px;
  margin-top: 0.5rem;
}

.pod {
  aspect-ratio: 1;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.6rem;
  font-weight: 600;
  text-align: center;
  color: white;
  text-shadow: 0 1px 2px rgba(0,0,0,0.3);
  position: relative;
  cursor: pointer;
  transition: transform 0.15s, box-shadow 0.15s;
  line-height: 1.1;
  padding: 2px;
  border: 2px solid rgba(0,0,0,0.15);
}

.pod:hover {
  transform: scale(1.08);
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  z-index: 2;
}

.pod.empty {
  background: #8B7355;
  opacity: 0.4;
  cursor: default;
}

.pod.empty:hover { transform: none; box-shadow: none; }

.pod.tomato { background: linear-gradient(135deg, #C0392B, #96281B); }
.pod.pepper { background: linear-gradient(135deg, #E74C3C, #C0392B); }
.pod.herb { background: linear-gradient(135deg, #27AE60, #1E8449); }
.pod.greens { background: linear-gradient(135deg, #2ECC71, #27AE60); }
.pod.squash { background: linear-gradient(135deg, #F39C12, #D68910); }
.pod.brassica { background: linear-gradient(135deg, #3498DB, #2471A3); }
.pod.eggplant { background: linear-gradient(135deg, #8E44AD, #6C3483); }
.pod.flower { background: linear-gradient(135deg, #E91E63, #C2185B); }
.pod.lemongrass { background: linear-gradient(135deg, #8BC34A, #689F38); }
.pod.chili { background: linear-gradient(135deg, #FF5722, #D84315); }
.pod.asparagus { background: linear-gradient(135deg, #4CAF50, #2E7D32); }

/* ====== PLANT CARDS ====== */
.plant-cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.25rem;
}

.plant-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid var(--cream-dark);
  transition: transform 0.2s, box-shadow 0.2s;
}

.plant-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
}

.plant-card-img {
  height: 160px;
  background-size: cover;
  background-position: center;
  position: relative;
}

.plant-card-img .count-badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background: rgba(0,0,0,0.65);
  color: white;
  padding: 0.25rem 0.6rem;
  border-radius: 100px;
  font-size: 0.75rem;
  font-weight: 600;
  backdrop-filter: blur(4px);
}

.plant-card-img .type-badge {
  position: absolute;
  bottom: 10px;
  left: 10px;
  padding: 0.2rem 0.6rem;
  border-radius: 100px;
  font-size: 0.7rem;
  font-weight: 600;
  color: white;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.plant-card-body { padding: 1rem; }
.plant-card-body h4 {
  font-family: 'DM Serif Display', serif;
  font-size: 1.1rem;
  color: var(--soil);
  margin-bottom: 0.5rem;
}

.plant-meta {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.4rem;
  margin-top: 0.75rem;
}

.plant-meta-item {
  font-size: 0.75rem;
  color: var(--text-light);
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.plant-meta-item strong { color: var(--text); font-weight: 600; }

.plant-schedule {
  margin-top: 0.75rem;
  padding-top: 0.75rem;
  border-top: 1px solid var(--cream-dark);
}

.schedule-bar {
  height: 8px;
  border-radius: 4px;
  background: var(--cream-dark);
  margin-top: 0.4rem;
  position: relative;
  overflow: hidden;
}

.schedule-fill {
  position: absolute;
  top: 0;
  height: 100%;
  border-radius: 4px;
}

.schedule-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.65rem;
  color: var(--text-light);
  margin-top: 0.3rem;
}

/* ====== GARDEN MAP ====== */
.garden-container {
  overflow-x: auto;
  padding: 1rem 0;
}

.garden-bed {
  min-width: 800px;
  background: #5C4033;
  border-radius: 12px;
  padding: 1.5rem;
  position: relative;
  border: 3px solid #3E2723;
}

.garden-bed-label {
  text-align: center;
  color: var(--cream);
  font-size: 0.75rem;
  font-weight: 500;
  margin-bottom: 0.75rem;
  opacity: 0.7;
}

.garden-row {
  display: flex;
  align-items: center;
  margin-bottom: 4px;
}

.row-label {
  width: 30px;
  font-size: 0.65rem;
  color: var(--cream);
  opacity: 0.5;
  text-align: right;
  padding-right: 8px;
  flex-shrink: 0;
}

.garden-cells {
  display: flex;
  flex: 1;
  gap: 2px;
}

.garden-cell {
  flex: 1;
  height: 20px;
  border-radius: 3px;
  cursor: pointer;
  transition: all 0.15s;
  position: relative;
}

.garden-cell:hover {
  transform: scaleY(1.3);
  z-index: 2;
}

.garden-cell.soil-empty { background: #6D4C30; opacity: 0.5; }
.garden-cell.plant-tomato { background: #C0392B; }
.garden-cell.plant-pepper { background: #E74C3C; }
.garden-cell.plant-herb { background: #27AE60; }
.garden-cell.plant-greens { background: #2ECC71; }
.garden-cell.plant-squash { background: #F39C12; }
.garden-cell.plant-brassica { background: #3498DB; }
.garden-cell.plant-eggplant { background: #8E44AD; }
.garden-cell.plant-flower { background: #E91E63; }
.garden-cell.plant-lemongrass { background: #8BC34A; }
.garden-cell.plant-chili { background: #FF5722; }
.garden-cell.plant-asparagus { background: #4CAF50; }

.sun-indicator {
  position: absolute;
  right: -40px;
  top: 0;
  bottom: 0;
  width: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
}

.garden-legend {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-top: 1.25rem;
  padding-top: 1rem;
  border-top: 1px solid rgba(255,255,255,0.1);
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 0.35rem;
  font-size: 0.72rem;
  color: var(--cream);
  opacity: 0.85;
}

.legend-swatch {
  width: 14px;
  height: 14px;
  border-radius: 4px;
  border: 1px solid rgba(255,255,255,0.2);
}

.compass {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 0;
  font-size: 0.75rem;
  color: var(--text-light);
  min-width: 800px;
}

.compass span { font-weight: 600; }

/* ====== PLANTING TIMELINE ====== */
.timeline-container { overflow-x: auto; }

.timeline {
  min-width: 800px;
  position: relative;
}

.timeline-header {
  display: grid;
  grid-template-columns: 180px repeat(8, 1fr);
  gap: 0;
  margin-bottom: 0.5rem;
}

.timeline-month {
  text-align: center;
  font-size: 0.72rem;
  font-weight: 600;
  color: var(--text-light);
  text-transform: uppercase;
  letter-spacing: 0.5px;
  padding: 0.5rem 0;
  border-bottom: 2px solid var(--cream-dark);
}

.timeline-month.current { color: var(--leaf-dark); border-color: var(--leaf); }

.timeline-row {
  display: grid;
  grid-template-columns: 180px repeat(8, 1fr);
  gap: 0;
  align-items: center;
  padding: 0.5rem 0;
  border-bottom: 1px solid rgba(0,0,0,0.04);
}

.timeline-plant-name {
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--text);
  padding-right: 1rem;
}

.timeline-cell {
  height: 28px;
  position: relative;
  display: flex;
  align-items: center;
}

.timeline-bar {
  height: 12px;
  border-radius: 6px;
  position: absolute;
  opacity: 0.85;
}

.timeline-bar.indoor { background: var(--frost-blue); }
.timeline-bar.transplant { background: var(--sun); }
.timeline-bar.outdoor { background: var(--leaf); }
.timeline-bar.harvest { background: var(--tomato); }

.timeline-now {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--tomato);
  z-index: 5;
}

.timeline-legend {
  display: flex;
  gap: 1.5rem;
  margin-top: 1rem;
  flex-wrap: wrap;
}

.timeline-legend-item {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.78rem;
  color: var(--text-light);
}

.timeline-legend-swatch {
  width: 20px;
  height: 8px;
  border-radius: 4px;
}

/* ====== PLANTING CALENDAR TABLE ====== */
.calendar-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.82rem;
}

.calendar-table th {
  text-align: left;
  padding: 0.6rem 0.8rem;
  border-bottom: 2px solid var(--cream-dark);
  font-weight: 600;
  color: var(--text-light);
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.calendar-table td {
  padding: 0.7rem 0.8rem;
  border-bottom: 1px solid var(--cream-dark);
  vertical-align: middle;
}

.calendar-table tr:hover td { background: rgba(74,124,89,0.04); }

.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  display: inline-block;
  margin-right: 0.4rem;
}

.status-dot.ready { background: var(--alert-green); }
.status-dot.soon { background: var(--alert-yellow); }
.status-dot.wait { background: var(--frost-blue); }

/* ====== TOOLTIP ====== */
.tooltip {
  display: none;
  position: fixed;
  background: var(--soil);
  color: var(--cream);
  padding: 0.6rem 0.9rem;
  border-radius: 8px;
  font-size: 0.78rem;
  z-index: 1000;
  pointer-events: none;
  max-width: 220px;
  line-height: 1.4;
  box-shadow: 0 8px 24px rgba(0,0,0,0.25);
}

.tooltip.show { display: block; }

/* ====== LOADING ====== */
.loading {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--text-light);
  font-size: 0.85rem;
}

.loading-spinner {
  width: 18px;
  height: 18px;
  border: 2px solid var(--cream-dark);
  border-top-color: var(--leaf);
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

/* ====== RESPONSIVE ====== */
@media (max-width: 768px) {
  .hero { padding: 2rem 1rem 1.5rem; }
  .section-card { padding: 1.25rem; }
  .tray-grid { grid-template-columns: 1fr; }
  .plant-cards { grid-template-columns: 1fr; }
  .weather-forecast { display: none; }
  .nav-tabs { padding: 1rem 1rem 0; }
  .section { padding: 0 1rem 2rem; }
}

/* ====== ANIMATIONS ====== */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to { opacity: 1; transform: translateY(0); }
}

.section.active .section-card { animation: fadeIn 0.3s ease; }

.plant-card { animation: fadeIn 0.3s ease backwards; }
.plant-card:nth-child(2) { animation-delay: 0.05s; }
.plant-card:nth-child(3) { animation-delay: 0.1s; }
.plant-card:nth-child(4) { animation-delay: 0.15s; }
.plant-card:nth-child(5) { animation-delay: 0.2s; }
.plant-card:nth-child(6) { animation-delay: 0.25s; }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <div class="hero-content">
    <h1>Joe's <span>Garden Planner</span></h1>
    <div class="hero-meta">
      <span class="badge">📍 Lawrence, KS</span>
      <span class="badge">🌱 Zone 6b</span>
      <span class="badge">📐 25′ × 4′ Bed</span>
      <span class="badge">❄️ Last Frost ~Apr 15</span>
      <span class="badge" id="seedCount">🌰 45 Seeds</span>
    </div>
  </div>
</div>

<!-- WEATHER BAR -->
<div class="weather-bar">
  <div class="weather-inner" id="weatherBar">
    <div class="loading" id="weatherLoading">
      <div class="loading-spinner"></div>
      Fetching weather for Lawrence, KS...
    </div>
  </div>
</div>

<!-- NAV TABS -->
<div class="nav-tabs" id="navTabs">
  <button class="tab-btn active" data-tab="trays">🌱 Seed Trays</button>
  <button class="tab-btn" data-tab="plants">🪴 Plant Guide</button>
  <button class="tab-btn" data-tab="garden">🗺️ Garden Layout</button>
  <button class="tab-btn" data-tab="schedule">📅 Planting Schedule</button>
</div>

<!-- SEED TRAYS -->
<div class="section active" id="trays">
  <div class="section-card">
    <h2>Seed Trays Overview</h2>
    <p style="color:var(--text-light); font-size:0.88rem; margin-bottom:1.25rem;">
      5 trays × 10 pods (2 wide × 5 long). Hover over any pod for plant details.
    </p>
    <div class="tray-grid" id="trayGrid"></div>
  </div>
</div>

<!-- PLANT GUIDE -->
<div class="section" id="plants">
  <div class="section-card">
    <h2>Plant Reference Guide</h2>
    <p style="color:var(--text-light); font-size:0.88rem; margin-bottom:1.25rem;">
      Complete growing info for each plant in your trays. Spacing, sun, and timing for Zone 6b.
    </p>
    <div class="plant-cards" id="plantCards"></div>
  </div>
</div>

<!-- GARDEN LAYOUT -->
<div class="section" id="garden">
  <div class="section-card">
    <h2>Optimized Garden Layout</h2>
    <p style="color:var(--text-light); font-size:0.88rem; margin-bottom:1rem;">
      25′ long × 4′ wide bed. Right side (east) gets the most sun. Plants arranged for optimal spacing, companion planting, and sun exposure. Each cell represents approximately 6″ × 6″.
    </p>
    <div class="compass">
      <span>← WEST (more shade)</span>
      <span>EAST (full sun) →</span>
    </div>
    <div class="garden-container">
      <div class="garden-bed" id="gardenBed"></div>
    </div>
  </div>
</div>

<!-- SCHEDULE -->
<div class="section" id="schedule">
  <div class="section-card">
    <h2>Planting Schedule</h2>
    <p style="color:var(--text-light); font-size:0.88rem; margin-bottom:1rem;">
      Timeline based on Lawrence, KS Zone 6b with average last frost date of April 15. Adjusted for current weather predictions.
    </p>
    <div class="timeline-container" id="timelineContainer"></div>
    <div class="timeline-legend">
      <div class="timeline-legend-item"><div class="timeline-legend-swatch" style="background:var(--frost-blue)"></div>Start Indoors</div>
      <div class="timeline-legend-item"><div class="timeline-legend-swatch" style="background:var(--sun)"></div>Harden Off/Transplant</div>
      <div class="timeline-legend-item"><div class="timeline-legend-swatch" style="background:var(--leaf)"></div>Direct Sow Outdoors</div>
      <div class="timeline-legend-item"><div class="timeline-legend-swatch" style="background:var(--tomato)"></div>Harvest Window</div>
    </div>
  </div>
  <div class="section-card">
    <h2>Detailed Planting Calendar</h2>
    <table class="calendar-table" id="calendarTable">
      <thead>
        <tr>
          <th>Plant</th>
          <th>Count</th>
          <th>Start Indoors</th>
          <th>Transplant Out</th>
          <th>Direct Sow</th>
          <th>Spacing</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody id="calendarBody"></tbody>
    </table>
  </div>
</div>

<!-- TOOLTIP -->
<div class="tooltip" id="tooltip"></div>

<script>
// =========================================================
// DATA
// =========================================================
const PLANTS = {
  cherokee_purple: {
    name: "Cherokee Purple Tomato",
    short: "Cherokee\nPurple",
    count: 4, tray: 1, type: "tomato", category: "Tomato",
    img: "https://images.unsplash.com/photo-1592841200221-a6898f307baa?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (8+ hrs)",
    water: "1-2\" per week", days_to_harvest: "80-90 days",
    description: "Large, dusky rose-purple beefsteak with rich, sweet, complex flavor. Indeterminate heirloom.",
    indoor_start_weeks_before_frost: 8,
    transplant_weeks_after_frost: 1,
    harvest_start_weeks_after_transplant: 12,
    harvest_duration_weeks: 8,
    sun_needs: "high",
    companion: ["basil", "pepper"],
    garden_class: "plant-tomato"
  },
  korean_long: {
    name: "Korean Long Tomato",
    short: "Korean\nLong",
    count: 2, tray: 1, type: "tomato", category: "Tomato",
    img: "https://images.unsplash.com/photo-1558818498-28c1e002b655?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (8+ hrs)",
    water: "1-2\" per week", days_to_harvest: "75-85 days",
    description: "Elongated paste-type tomato perfect for sauces. Prolific producer with meaty flesh.",
    indoor_start_weeks_before_frost: 8,
    transplant_weeks_after_frost: 1,
    harvest_start_weeks_after_transplant: 11,
    harvest_duration_weeks: 8,
    sun_needs: "high",
    companion: ["basil", "pepper"],
    garden_class: "plant-tomato"
  },
  yellow_tiger: {
    name: "Yellow Tiger Tomato",
    short: "Yellow\nTiger",
    count: 2, tray: 1, type: "tomato", category: "Tomato",
    img: "https://images.unsplash.com/photo-1582284540020-8acbe03f4924?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (8+ hrs)",
    water: "1-2\" per week", days_to_harvest: "70-80 days",
    description: "Stunning striped yellow-orange cherry tomato. Sweet and tangy with beautiful presentation.",
    indoor_start_weeks_before_frost: 8,
    transplant_weeks_after_frost: 1,
    harvest_start_weeks_after_transplant: 10,
    harvest_duration_weeks: 10,
    sun_needs: "high",
    companion: ["basil", "pepper"],
    garden_class: "plant-tomato"
  },
  red_pepper: {
    name: "Red Pepper",
    short: "Red\nPepper",
    count: 2, tray: 1, type: "pepper", category: "Pepper",
    img: "https://images.unsplash.com/photo-1563565375-f3fdfdbefa83?w=400&h=200&fit=crop",
    spacing_in: 18, rows_needed: 1, sun: "Full Sun (6-8 hrs)",
    water: "1-2\" per week", days_to_harvest: "70-90 days",
    description: "Classic sweet red bell pepper. Starts green and ripens to vibrant red.",
    indoor_start_weeks_before_frost: 10,
    transplant_weeks_after_frost: 2,
    harvest_start_weeks_after_transplant: 10,
    harvest_duration_weeks: 8,
    sun_needs: "high",
    companion: ["tomato", "basil"],
    garden_class: "plant-pepper"
  },
  lemongrass: {
    name: "Lemongrass",
    short: "Lemon-\ngrass",
    count: 4, tray: 2, type: "lemongrass", category: "Herb",
    img: "https://images.unsplash.com/photo-1596547609652-9cf5d8c76921?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (6-8 hrs)",
    water: "Regular, moist soil", days_to_harvest: "75-100 days",
    description: "Aromatic tropical grass used in Thai and Vietnamese cooking. Also a natural mosquito repellent.",
    indoor_start_weeks_before_frost: 8,
    transplant_weeks_after_frost: 3,
    harvest_start_weeks_after_transplant: 12,
    harvest_duration_weeks: 12,
    sun_needs: "high",
    companion: [],
    garden_class: "plant-lemongrass"
  },
  thai_birds_eye: {
    name: "Thai Bird's Eye Chili",
    short: "Bird's\nEye",
    count: 4, tray: 2, type: "chili", category: "Pepper",
    img: "https://images.unsplash.com/photo-1588252303782-cb80119abd6d?w=400&h=200&fit=crop",
    spacing_in: 18, rows_needed: 1, sun: "Full Sun (6-8 hrs)",
    water: "1\" per week", days_to_harvest: "90-120 days",
    description: "Fiery small chili peppers (50,000-100,000 SHU). Essential for Thai cuisine. Very prolific.",
    indoor_start_weeks_before_frost: 10,
    transplant_weeks_after_frost: 2,
    harvest_start_weeks_after_transplant: 14,
    harvest_duration_weeks: 10,
    sun_needs: "high",
    companion: ["tomato", "basil"],
    garden_class: "plant-chili"
  },
  wasabi_arugula: {
    name: "Wasabi Arugula",
    short: "Wasabi\nArugula",
    count: 2, tray: 3, type: "greens", category: "Greens",
    img: "https://images.unsplash.com/photo-1622206151226-18ca2c9ab4a1?w=400&h=200&fit=crop",
    spacing_in: 6, rows_needed: 1, sun: "Partial to Full Sun",
    water: "Regular, even moisture", days_to_harvest: "21-40 days",
    description: "Spicy, wasabi-flavored arugula with intense peppery kick. Fast-growing cool-season green.",
    indoor_start_weeks_before_frost: 0,
    transplant_weeks_after_frost: -4,
    direct_sow_weeks_before_frost: 4,
    harvest_start_weeks_after_transplant: 4,
    harvest_duration_weeks: 6,
    sun_needs: "medium",
    companion: [],
    garden_class: "plant-greens"
  },
  yod_fai: {
    name: "Yod Fai (Water Spinach Tips)",
    short: "Yod\nFai",
    count: 4, tray: 3, type: "greens", category: "Greens",
    img: "https://images.unsplash.com/photo-1540420773420-3366772f4999?w=400&h=200&fit=crop",
    spacing_in: 12, rows_needed: 1, sun: "Full Sun (6+ hrs)",
    water: "Heavy — loves moisture", days_to_harvest: "40-60 days",
    description: "Thai water spinach / morning glory tips. Stir-fry staple. Grows quickly in warm weather.",
    indoor_start_weeks_before_frost: 6,
    transplant_weeks_after_frost: 3,
    harvest_start_weeks_after_transplant: 6,
    harvest_duration_weeks: 14,
    sun_needs: "high",
    companion: [],
    garden_class: "plant-greens"
  },
  asparagus: {
    name: "Asparagus",
    short: "Aspar-\nagus",
    count: 4, tray: 3, type: "asparagus", category: "Perennial Veg",
    img: "https://images.unsplash.com/photo-1515471209610-dae1c92d8777?w=400&h=200&fit=crop",
    spacing_in: 18, rows_needed: 1, sun: "Full Sun (8+ hrs)",
    water: "1-2\" per week", days_to_harvest: "2-3 years (perennial)",
    description: "Long-lived perennial. Won't produce full harvest for 2-3 years but will come back every spring for 20+ years.",
    indoor_start_weeks_before_frost: 12,
    transplant_weeks_after_frost: 0,
    harvest_start_weeks_after_transplant: 104,
    harvest_duration_weeks: 8,
    sun_needs: "high",
    companion: ["tomato"],
    garden_class: "plant-asparagus"
  },
  brussel_sprouts: {
    name: "Brussels Sprouts",
    short: "Brussels\nSprouts",
    count: 2, tray: 4, type: "brassica", category: "Brassica",
    img: "https://images.unsplash.com/photo-1438118907704-7718ee9a191a?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (6+ hrs)",
    water: "1-1.5\" per week", days_to_harvest: "90-120 days",
    description: "Cool-season brassica that sweetens after frost. Plant for fall harvest in Zone 6b.",
    indoor_start_weeks_before_frost: 6,
    transplant_weeks_after_frost: -2,
    harvest_start_weeks_after_transplant: 16,
    harvest_duration_weeks: 6,
    sun_needs: "medium",
    companion: [],
    garden_class: "plant-brassica"
  },
  yellow_squash: {
    name: "Yellow Squash",
    short: "Yellow\nSquash",
    count: 2, tray: 4, type: "squash", category: "Squash",
    img: "https://images.unsplash.com/photo-1596199019783-6dec94879fa9?w=400&h=200&fit=crop",
    spacing_in: 36, rows_needed: 2, sun: "Full Sun (8+ hrs)",
    water: "1-2\" per week", days_to_harvest: "50-65 days",
    description: "Prolific summer squash. Bush variety works in tighter spaces. Harvest young for best flavor.",
    indoor_start_weeks_before_frost: 3,
    transplant_weeks_after_frost: 2,
    direct_sow_weeks_after_frost: 2,
    harvest_start_weeks_after_transplant: 7,
    harvest_duration_weeks: 10,
    sun_needs: "high",
    companion: [],
    garden_class: "plant-squash"
  },
  nagasaki_eggplant: {
    name: "Nagasaki Long Eggplant",
    short: "Nagasaki\nEggplant",
    count: 2, tray: 4, type: "eggplant", category: "Nightshade",
    img: "https://images.unsplash.com/photo-1615484477778-ca3b77940c25?w=400&h=200&fit=crop",
    spacing_in: 24, rows_needed: 1, sun: "Full Sun (6-8 hrs)",
    water: "1-2\" per week", days_to_harvest: "65-80 days",
    description: "Japanese long eggplant with tender, creamy flesh. Less bitter than globe types. Great for grilling.",
    indoor_start_weeks_before_frost: 10,
    transplant_weeks_after_frost: 3,
    harvest_start_weeks_after_transplant: 10,
    harvest_duration_weeks: 8,
    sun_needs: "high",
    companion: ["pepper"],
    garden_class: "plant-eggplant"
  },
  thai_basil: {
    name: "Thai Basil",
    short: "Thai\nBasil",
    count: 4, tray: 4, type: "herb", category: "Herb",
    img: "https://images.unsplash.com/photo-1618375569909-3c8616cf7733?w=400&h=200&fit=crop",
    spacing_in: 12, rows_needed: 1, sun: "Full Sun (6-8 hrs)",
    water: "Regular, even moisture", days_to_harvest: "60-90 days",
    description: "Aromatic herb with anise/licorice flavor. Essential for Thai curries, pho, and stir-fries.",
    indoor_start_weeks_before_frost: 6,
    transplant_weeks_after_frost: 2,
    harvest_start_weeks_after_transplant: 8,
    harvest_duration_weeks: 14,
    sun_needs: "high",
    companion: ["tomato", "pepper"],
    garden_class: "plant-herb"
  },
  cilantro: {
    name: "Cilantro",
    short: "Cilantro",
    count: 3, tray: 5, type: "herb", category: "Herb",
    img: "https://images.unsplash.com/photo-1526346698789-22fd84314424?w=400&h=200&fit=crop",
    spacing_in: 6, rows_needed: 1, sun: "Partial to Full Sun",
    water: "Regular, even moisture", days_to_harvest: "45-70 days",
    description: "Cool-season herb that bolts in heat. Succession plant every 3 weeks. Seeds become coriander.",
    indoor_start_weeks_before_frost: 0,
    direct_sow_weeks_before_frost: 2,
    transplant_weeks_after_frost: -2,
    harvest_start_weeks_after_transplant: 6,
    harvest_duration_weeks: 4,
    sun_needs: "low",
    companion: [],
    garden_class: "plant-herb"
  },
  wildflowers: {
    name: "Wildflowers",
    short: "Wild-\nflowers",
    count: 2, tray: 5, type: "flower", category: "Flower",
    img: "https://images.unsplash.com/photo-1490750967868-88aa4f44baee?w=400&h=200&fit=crop",
    spacing_in: 12, rows_needed: 1, sun: "Full Sun",
    water: "Low once established", days_to_harvest: "60-90 days to bloom",
    description: "Native pollinator mix attracts beneficial insects. Great border plant for pest control.",
    indoor_start_weeks_before_frost: 0,
    direct_sow_weeks_before_frost: 2,
    transplant_weeks_after_frost: 0,
    harvest_start_weeks_after_transplant: 10,
    harvest_duration_weeks: 16,
    sun_needs: "medium",
    companion: [],
    garden_class: "plant-flower"
  }
};

// Tray configurations (2 wide x 5 rows = 10 pods each)
const TRAYS = [
  {
    label: "Tray 1",
    pods: [
      "cherokee_purple","cherokee_purple",
      "cherokee_purple","cherokee_purple",
      "korean_long","korean_long",
      "yellow_tiger","yellow_tiger",
      "red_pepper","red_pepper"
    ]
  },
  {
    label: "Tray 2",
    pods: [
      "lemongrass","lemongrass",
      "lemongrass","lemongrass",
      "thai_birds_eye","thai_birds_eye",
      "thai_birds_eye","thai_birds_eye",
      null, null
    ]
  },
  {
    label: "Tray 3",
    pods: [
      "wasabi_arugula","wasabi_arugula",
      "yod_fai","yod_fai",
      "yod_fai","yod_fai",
      "asparagus","asparagus",
      "asparagus","asparagus"
    ]
  },
  {
    label: "Tray 4",
    pods: [
      "brussel_sprouts","brussel_sprouts",
      "yellow_squash","yellow_squash",
      "nagasaki_eggplant","nagasaki_eggplant",
      "thai_basil","thai_basil",
      "thai_basil","thai_basil"
    ]
  },
  {
    label: "Tray 5",
    pods: [
      "cilantro","cilantro",
      "cilantro",null,
      "wildflowers","wildflowers",
      null,null,
      null,null
    ]
  }
];

// =========================================================
// WEATHER
// =========================================================
const LAWRENCE_LAT = 38.9717;
const LAWRENCE_LON = -95.2353;

const WMO_CODES = {
  0: { icon: "☀️", desc: "Clear sky" },
  1: { icon: "🌤️", desc: "Mainly clear" },
  2: { icon: "⛅", desc: "Partly cloudy" },
  3: { icon: "☁️", desc: "Overcast" },
  45: { icon: "🌫️", desc: "Foggy" },
  48: { icon: "🌫️", desc: "Depositing rime fog" },
  51: { icon: "🌦️", desc: "Light drizzle" },
  53: { icon: "🌦️", desc: "Moderate drizzle" },
  55: { icon: "🌧️", desc: "Dense drizzle" },
  61: { icon: "🌧️", desc: "Slight rain" },
  63: { icon: "🌧️", desc: "Moderate rain" },
  65: { icon: "🌧️", desc: "Heavy rain" },
  66: { icon: "🌨️", desc: "Light freezing rain" },
  67: { icon: "🌨️", desc: "Heavy freezing rain" },
  71: { icon: "❄️", desc: "Slight snow" },
  73: { icon: "❄️", desc: "Moderate snow" },
  75: { icon: "❄️", desc: "Heavy snow" },
  77: { icon: "🌨️", desc: "Snow grains" },
  80: { icon: "🌦️", desc: "Slight rain showers" },
  81: { icon: "🌧️", desc: "Moderate rain showers" },
  82: { icon: "🌧️", desc: "Violent rain showers" },
  85: { icon: "🌨️", desc: "Slight snow showers" },
  86: { icon: "🌨️", desc: "Heavy snow showers" },
  95: { icon: "⛈️", desc: "Thunderstorm" },
  96: { icon: "⛈️", desc: "Thunderstorm w/ slight hail" },
  99: { icon: "⛈️", desc: "Thunderstorm w/ heavy hail" }
};

async function fetchWeather() {
  try {
    const url = `https://api.open-meteo.com/v1/forecast?latitude=${LAWRENCE_LAT}&longitude=${LAWRENCE_LON}&current=temperature_2m,weather_code,wind_speed_10m&daily=weather_code,temperature_2m_max,temperature_2m_min&temperature_unit=fahrenheit&wind_speed_unit=mph&timezone=America/Chicago&forecast_days=7`;
    const resp = await fetch(url);
    const data = await resp.json();
    renderWeather(data);
  } catch (e) {
    document.getElementById('weatherLoading').innerHTML = '⚠️ Weather unavailable — check back later';
  }
}

function renderWeather(data) {
  const bar = document.getElementById('weatherBar');
  const current = data.current;
  const daily = data.daily;
  const wmo = WMO_CODES[current.weather_code] || { icon: "🌡️", desc: "Unknown" };
  const dayNames = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];

  // Check for frost alerts in the next 7 days
  let frostAlert = null;
  let minTemp = Infinity;
  let frostDayName = '';
  for (let i = 0; i < daily.temperature_2m_min.length; i++) {
    if (daily.temperature_2m_min[i] < minTemp) {
      minTemp = daily.temperature_2m_min[i];
      const d = new Date(daily.time[i]);
      frostDayName = dayNames[d.getDay()];
    }
  }

  if (minTemp <= 32) {
    frostAlert = { level: 'danger', msg: `🥶 FROST ALERT: Temperature dropping to ${Math.round(minTemp)}°F on ${frostDayName}. Protect tender seedlings or delay transplanting!` };
  } else if (minTemp <= 38) {
    frostAlert = { level: 'warning', msg: `⚠️ COOL NIGHTS AHEAD: Low of ${Math.round(minTemp)}°F on ${frostDayName}. Monitor tender plants and have row covers ready.` };
  } else {
    frostAlert = { level: 'safe', msg: `✅ No frost risk in the 7-day forecast. Lowest temp: ${Math.round(minTemp)}°F. Safe for warm-season transplants.` };
  }

  let forecastHTML = '';
  for (let i = 1; i < Math.min(6, daily.time.length); i++) {
    const d = new Date(daily.time[i]);
    const dayWmo = WMO_CODES[daily.weather_code[i]] || { icon: "🌡️" };
    forecastHTML += `
      <div class="forecast-day">
        <div class="day-name">${dayNames[d.getDay()]}</div>
        <div class="day-icon">${dayWmo.icon}</div>
        <div class="day-temps">${Math.round(daily.temperature_2m_max[i])}° / ${Math.round(daily.temperature_2m_min[i])}°</div>
      </div>`;
  }

  bar.innerHTML = `
    <div class="weather-current">
      <span style="font-size:2rem">${wmo.icon}</span>
      <div>
        <div class="weather-temp">${Math.round(current.temperature_2m)}°F</div>
        <div class="weather-desc">${wmo.desc} · Wind ${Math.round(current.wind_speed_10m)} mph</div>
      </div>
    </div>
    <div class="weather-forecast">${forecastHTML}</div>
    <div class="frost-alert ${frostAlert.level}">${frostAlert.msg}</div>
  `;
}

// =========================================================
// SEED TRAYS
// =========================================================
function renderTrays() {
  const grid = document.getElementById('trayGrid');
  grid.innerHTML = TRAYS.map((tray, ti) => {
    const pods = tray.pods.map((plantKey, pi) => {
      if (!plantKey) return `<div class="pod empty"></div>`;
      const p = PLANTS[plantKey];
      return `<div class="pod ${p.type}" data-plant="${plantKey}" onmouseenter="showTooltip(event, '${plantKey}')" onmouseleave="hideTooltip()">${p.short}</div>`;
    }).join('');
    return `
      <div class="tray">
        <div class="tray-label">${tray.label}</div>
        <div class="tray-pods">${pods}</div>
      </div>`;
  }).join('');
}

// =========================================================
// PLANT CARDS
// =========================================================
function renderPlantCards() {
  const container = document.getElementById('plantCards');
  const typeColors = {
    tomato: '#C0392B', pepper: '#E74C3C', herb: '#27AE60', greens: '#2ECC71',
    squash: '#F39C12', brassica: '#3498DB', eggplant: '#8E44AD', flower: '#E91E63',
    lemongrass: '#8BC34A', chili: '#FF5722', asparagus: '#4CAF50'
  };

  container.innerHTML = Object.entries(PLANTS).map(([key, p]) => {
    const now = new Date();
    const frostDate = new Date(now.getFullYear(), 3, 15); // April 15
    let statusText = '';
    let statusClass = '';

    if (p.indoor_start_weeks_before_frost > 0) {
      const startDate = new Date(frostDate);
      startDate.setDate(startDate.getDate() - p.indoor_start_weeks_before_frost * 7);
      if (now < startDate) {
        statusText = `Start indoors ${startDate.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })}`;
        statusClass = 'wait';
      } else if (now < frostDate) {
        statusText = 'Start indoors NOW';
        statusClass = 'ready';
      } else {
        statusText = 'Ready to transplant';
        statusClass = 'ready';
      }
    } else if (p.direct_sow_weeks_before_frost) {
      const sowDate = new Date(frostDate);
      sowDate.setDate(sowDate.getDate() - p.direct_sow_weeks_before_frost * 7);
      if (now >= sowDate) {
        statusText = 'Direct sow NOW';
        statusClass = 'ready';
      } else {
        statusText = `Direct sow ${sowDate.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })}`;
        statusClass = 'soon';
      }
    }

    return `
      <div class="plant-card">
        <div class="plant-card-img" style="background-image:url('${p.img}')">
          <span class="count-badge">×${p.count} plants</span>
          <span class="type-badge" style="background:${typeColors[p.type]}">${p.category}</span>
        </div>
        <div class="plant-card-body">
          <h4>${p.name}</h4>
          <p style="font-size:0.8rem; color:var(--text-light); line-height:1.4;">${p.description}</p>
          <div class="plant-meta">
            <div class="plant-meta-item">☀️ <strong>${p.sun}</strong></div>
            <div class="plant-meta-item">💧 <strong>${p.water}</strong></div>
            <div class="plant-meta-item">📏 <strong>${p.spacing_in}″ apart</strong></div>
            <div class="plant-meta-item">🕐 <strong>${p.days_to_harvest}</strong></div>
          </div>
          ${statusText ? `
          <div class="plant-schedule">
            <div style="font-size:0.78rem; display:flex; align-items:center;">
              <span class="status-dot ${statusClass}"></span>
              <strong>${statusText}</strong>
            </div>
          </div>` : ''}
        </div>
      </div>`;
  }).join('');
}

// =========================================================
// GARDEN LAYOUT (25ft x 4ft = 300in x 48in, using 6in cells = 50 cols x 8 rows)
// =========================================================
function renderGardenLayout() {
  const bed = document.getElementById('gardenBed');
  const COLS = 50; // 25ft / 6in
  const ROWS = 8;  // 4ft / 6in

  // Build layout grid — right side = more sun (higher column index)
  const grid = Array.from({ length: ROWS }, () => Array(COLS).fill(null));

  // Plant placement: right side = full sun, left = partial shade
  // Strategy: tallest plants on north side (top rows) to avoid shading
  // Sun-loving on right, shade-tolerant on left

  const placements = [
    // FULL SUN RIGHT SIDE: Tomatoes, Peppers, Eggplant, Squash
    // Row 0-1 (back/north): Tall tomatoes staked — won't shade others
    { key: 'cherokee_purple', row: 0, startCol: 38, spacing: 4 }, // 24" = 4 cells
    { key: 'korean_long', row: 0, startCol: 30, spacing: 4 },
    { key: 'yellow_tiger', row: 1, startCol: 38, spacing: 4 },

    // Row 2: Peppers and chilies
    { key: 'red_pepper', row: 2, startCol: 40, spacing: 3 },
    { key: 'thai_birds_eye', row: 2, startCol: 30, spacing: 3 },

    // Row 3: Eggplant and Lemongrass (tall)
    { key: 'nagasaki_eggplant', row: 3, startCol: 40, spacing: 4 },
    { key: 'lemongrass', row: 0, startCol: 18, spacing: 4 },

    // Row 4-5: Squash (needs space — 36" = 6 cells)
    { key: 'yellow_squash', row: 6, startCol: 34, spacing: 6 },

    // Row 4: Thai Basil (companion w/ tomatoes)
    { key: 'thai_basil', row: 1, startCol: 30, spacing: 2 },

    // Row 5: Asparagus (perennial, back corner)
    { key: 'asparagus', row: 0, startCol: 4, spacing: 3 },

    // LEFT/SHADE TOLERANT
    // Brussels sprouts (cool season, partial shade ok)
    { key: 'brussel_sprouts', row: 3, startCol: 4, spacing: 4 },

    // Cilantro (prefers some shade in KS heat)
    { key: 'cilantro', row: 5, startCol: 2, spacing: 1 },

    // Wasabi arugula (cool shade)
    { key: 'wasabi_arugula', row: 4, startCol: 2, spacing: 1 },

    // Yod Fai
    { key: 'yod_fai', row: 5, startCol: 10, spacing: 2 },

    // Wildflowers (border/pollinator strip)
    { key: 'wildflowers', row: 7, startCol: 20, spacing: 2 },
  ];

  placements.forEach(pl => {
    const plant = PLANTS[pl.key];
    for (let i = 0; i < plant.count; i++) {
      const col = pl.startCol + (i * pl.spacing);
      if (col < COLS && pl.row < ROWS) {
        grid[pl.row][col] = pl.key;
        // Fill adjacent cells based on spacing
        for (let s = 1; s < pl.spacing && (col + s) < COLS; s++) {
          if (!grid[pl.row][col + s]) grid[pl.row][col + s] = pl.key + '_fill';
        }
      }
    }
  });

  // Render garden
  const sunGradient = '→ ☀️';
  let html = `<div class="garden-bed-label">25 feet (each cell ≈ 6″) — North ↑</div>`;

  for (let r = 0; r < ROWS; r++) {
    html += `<div class="garden-row">`;
    html += `<div class="row-label">${r + 1}</div>`;
    html += `<div class="garden-cells">`;
    for (let c = 0; c < COLS; c++) {
      const cell = grid[r][c];
      if (cell) {
        const baseKey = cell.replace('_fill', '');
        const plant = PLANTS[baseKey];
        if (plant) {
          const isFill = cell.includes('_fill');
          html += `<div class="garden-cell ${plant.garden_class}" style="opacity:${isFill ? '0.45' : '0.85'}" data-plant="${baseKey}" onmouseenter="showTooltip(event, '${baseKey}')" onmouseleave="hideTooltip()"></div>`;
        } else {
          html += `<div class="garden-cell soil-empty"></div>`;
        }
      } else {
        html += `<div class="garden-cell soil-empty"></div>`;
      }
    }
    html += `</div>`;
    if (r === 0) html += `<div class="sun-indicator">☀️</div>`;
    else html += `<div class="sun-indicator" style="opacity:${0.3 + (0.7 * (1 - r/ROWS))}">☀️</div>`;
    html += `</div>`;
  }

  // Legend
  const legendItems = {};
  Object.entries(PLANTS).forEach(([k, p]) => {
    if (!legendItems[p.type]) legendItems[p.type] = { name: p.name, cls: p.garden_class };
  });

  html += `<div class="garden-legend">`;
  Object.entries(legendItems).forEach(([type, info]) => {
    const colors = {
      tomato: '#C0392B', pepper: '#E74C3C', herb: '#27AE60', greens: '#2ECC71',
      squash: '#F39C12', brassica: '#3498DB', eggplant: '#8E44AD', flower: '#E91E63',
      lemongrass: '#8BC34A', chili: '#FF5722', asparagus: '#4CAF50'
    };
    html += `<div class="legend-item"><div class="legend-swatch" style="background:${colors[type]}"></div>${type.charAt(0).toUpperCase() + type.slice(1)}</div>`;
  });
  html += `<div class="legend-item"><div class="legend-swatch" style="background:#6D4C30"></div>Open soil</div>`;
  html += `</div>`;

  bed.innerHTML = html;
}

// =========================================================
// PLANTING TIMELINE
// =========================================================
function renderTimeline() {
  const container = document.getElementById('timelineContainer');
  const months = ['Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct'];
  const now = new Date();
  const currentMonth = now.getMonth(); // 0-indexed

  const frostDate = new Date(now.getFullYear(), 3, 15); // April 15

  let html = `<div class="timeline"><div class="timeline-header"><div class="timeline-month">Plant</div>`;
  months.forEach((m, i) => {
    const monthIndex = i + 2; // March = 2
    html += `<div class="timeline-month ${monthIndex === currentMonth ? 'current' : ''}">${m}</div>`;
  });
  html += `</div>`;

  Object.entries(PLANTS).forEach(([key, p]) => {
    html += `<div class="timeline-row">`;
    html += `<div class="timeline-plant-name">${p.name}</div>`;

    // Calculate dates
    const indoorStart = new Date(frostDate);
    indoorStart.setDate(indoorStart.getDate() - (p.indoor_start_weeks_before_frost || 0) * 7);

    const transplantDate = new Date(frostDate);
    transplantDate.setDate(transplantDate.getDate() + (p.transplant_weeks_after_frost || 0) * 7);

    const harvestStart = new Date(transplantDate);
    harvestStart.setDate(harvestStart.getDate() + (p.harvest_start_weeks_after_transplant || 0) * 7);

    const harvestEnd = new Date(harvestStart);
    harvestEnd.setDate(harvestEnd.getDate() + (p.harvest_duration_weeks || 0) * 7);

    // Convert dates to percentage positions (March 1 = 0%, October 31 = 100%)
    const rangeStart = new Date(now.getFullYear(), 2, 1); // March 1
    const rangeEnd = new Date(now.getFullYear(), 9, 31); // October 31
    const totalDays = (rangeEnd - rangeStart) / (1000 * 60 * 60 * 24);

    function dateToPct(d) {
      const days = (d - rangeStart) / (1000 * 60 * 60 * 24);
      return Math.max(0, Math.min(100, (days / totalDays) * 100));
    }

    for (let i = 0; i < months.length; i++) {
      html += `<div class="timeline-cell">`;

      // Indoor bar
      if (p.indoor_start_weeks_before_frost > 0) {
        const cellStart = (i / months.length) * 100;
        const cellEnd = ((i + 1) / months.length) * 100;
        const barStart = dateToPct(indoorStart);
        const barEnd = dateToPct(transplantDate);

        if (barStart < cellEnd && barEnd > cellStart) {
          const left = Math.max(0, (barStart - cellStart) / (cellEnd - cellStart) * 100);
          const right = Math.min(100, (barEnd - cellStart) / (cellEnd - cellStart) * 100);
          html += `<div class="timeline-bar indoor" style="left:${left}%;width:${right-left}%"></div>`;
        }
      }

      // Outdoor bar
      {
        const cellStart = (i / months.length) * 100;
        const cellEnd = ((i + 1) / months.length) * 100;
        const barStart = dateToPct(transplantDate);
        const barEnd = dateToPct(harvestStart);

        if (barStart < cellEnd && barEnd > cellStart) {
          const left = Math.max(0, (barStart - cellStart) / (cellEnd - cellStart) * 100);
          const right = Math.min(100, (barEnd - cellStart) / (cellEnd - cellStart) * 100);
          html += `<div class="timeline-bar outdoor" style="left:${left}%;width:${right-left}%"></div>`;
        }
      }

      // Harvest bar
      if (p.harvest_start_weeks_after_transplant < 100) {
        const cellStart = (i / months.length) * 100;
        const cellEnd = ((i + 1) / months.length) * 100;
        const barStart = dateToPct(harvestStart);
        const barEnd = dateToPct(harvestEnd);

        if (barStart < cellEnd && barEnd > cellStart) {
          const left = Math.max(0, (barStart - cellStart) / (cellEnd - cellStart) * 100);
          const right = Math.min(100, (barEnd - cellStart) / (cellEnd - cellStart) * 100);
          html += `<div class="timeline-bar harvest" style="left:${left}%;width:${right-left}%"></div>`;
        }
      }

      html += `</div>`;
    }

    html += `</div>`;
  });

  html += `</div>`;
  container.innerHTML = html;
}

// =========================================================
// CALENDAR TABLE
// =========================================================
function renderCalendar() {
  const body = document.getElementById('calendarBody');
  const now = new Date();
  const frostDate = new Date(now.getFullYear(), 3, 15);

  body.innerHTML = Object.entries(PLANTS).map(([key, p]) => {
    const indoorStart = new Date(frostDate);
    indoorStart.setDate(indoorStart.getDate() - (p.indoor_start_weeks_before_frost || 0) * 7);

    const transplantDate = new Date(frostDate);
    transplantDate.setDate(transplantDate.getDate() + (p.transplant_weeks_after_frost || 0) * 7);

    const directSow = p.direct_sow_weeks_before_frost
      ? (() => { const d = new Date(frostDate); d.setDate(d.getDate() - p.direct_sow_weeks_before_frost * 7); return d; })()
      : (p.direct_sow_weeks_after_frost
        ? (() => { const d = new Date(frostDate); d.setDate(d.getDate() + p.direct_sow_weeks_after_frost * 7); return d; })()
        : null);

    const fmt = d => d ? d.toLocaleDateString('en-US', { month: 'short', day: 'numeric' }) : '—';

    // Status
    let statusText = '', statusClass = '';
    if (p.indoor_start_weeks_before_frost > 0 && now >= indoorStart && now < transplantDate) {
      statusText = 'Start Indoors'; statusClass = 'ready';
    } else if (now >= transplantDate && now < new Date(transplantDate.getTime() + 14 * 86400000)) {
      statusText = 'Transplant Now'; statusClass = 'ready';
    } else if (now < indoorStart) {
      statusText = 'Upcoming'; statusClass = 'wait';
    } else {
      statusText = 'Growing'; statusClass = 'soon';
    }

    return `<tr>
      <td><strong>${p.name}</strong></td>
      <td>${p.count}</td>
      <td>${p.indoor_start_weeks_before_frost > 0 ? fmt(indoorStart) : '—'}</td>
      <td>${fmt(transplantDate)}</td>
      <td>${directSow ? fmt(directSow) : '—'}</td>
      <td>${p.spacing_in}″</td>
      <td><span class="status-dot ${statusClass}"></span>${statusText}</td>
    </tr>`;
  }).join('');
}

// =========================================================
// TOOLTIP
// =========================================================
function showTooltip(e, plantKey) {
  const p = PLANTS[plantKey];
  if (!p) return;
  const tip = document.getElementById('tooltip');
  tip.innerHTML = `<strong>${p.name}</strong><br>${p.sun}<br>Spacing: ${p.spacing_in}″<br>Harvest: ${p.days_to_harvest}<br>Count: ${p.count} plants`;
  tip.classList.add('show');
  tip.style.left = (e.clientX + 12) + 'px';
  tip.style.top = (e.clientY - 12) + 'px';
}

function hideTooltip() {
  document.getElementById('tooltip').classList.remove('show');
}

document.addEventListener('mousemove', (e) => {
  const tip = document.getElementById('tooltip');
  if (tip.classList.contains('show')) {
    tip.style.left = (e.clientX + 12) + 'px';
    tip.style.top = (e.clientY - 12) + 'px';
  }
});

// =========================================================
// TAB NAVIGATION
// =========================================================
document.getElementById('navTabs').addEventListener('click', (e) => {
  if (!e.target.classList.contains('tab-btn')) return;
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  e.target.classList.add('active');
  document.getElementById(e.target.dataset.tab).classList.add('active');
});

// =========================================================
// INIT
// =========================================================
fetchWeather();
renderTrays();
renderPlantCards();
renderGardenLayout();
renderTimeline();
renderCalendar();

// Refresh weather every 30 minutes
setInterval(fetchWeather, 30 * 60 * 1000);
</script>
</body>
</html>
