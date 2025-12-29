# Adaptive-Radial-Dropdown-Gauge
A compact and expandable radial chart/gauge pattern for Home Assistant, designed for comparing multiple values (TRVs, temperature, humidity, batteries) with automatic cleanup.


A reusable **compact → expandable radial chart / gauge pattern** for Home Assistant dashboards.

This pattern is designed for **comparing multiple values at a glance**, with the option to expand into a more detailed view when needed — and automatically tidy itself up afterwards.

Although the example implementation uses **TRV valve positions**, the pattern works equally well for:

- Temperature comparisons
- Humidity levels
- Battery percentages
- Energy usage by zone
- Any bounded numeric sensor data

---

## What problem this solves

Most dashboards struggle with a trade-off:

- Compact views are easy to scan, but lack detail  
- Detailed views are useful, but clutter the UI  

This pattern gives you both:

- A **small “Now” snapshot** by default
- A **tap-to-expand detailed comparison**
- Optional **auto-close behaviour** so expanded views don’t linger

It’s particularly effective on **tablets, wall panels, and dense dashboards**.

---

## Core features

- Radial comparison chart using ApexCharts
- Single boolean-driven expand / collapse
- Optional auto-close timer
- Optional “Hold / Pin Open” override
- Optional auto-close on navigation (Browser Mod)
- Fully reusable for other sensor types

---

## Requirements

Install via HACS:

- **ApexCharts Card**
- **Button Card**

Optional:

- **Browser Mod** (only if you want auto-close on navigation)

---

## Installation

### 1️⃣ Install the package

Copy the file:

packages/adaptive_radial_dropdown_gauge.yaml

Into your Home Assistant config:


Ensure packages are enabled in `configuration.yaml`:

homeassistant:
  packages: !include_dir_named packages

2️⃣ Add the Lovelace card
Copy:

lovelace/adaptive_radial_dropdown_gauge_card.yaml

Paste it into any dashboard using a manual YAML card.
Replace the placeholder sensor entities with your own.
How the dropdown behaviour works
Expand / collapse
A single helper controls visibility:
input_boolean.radial_gauge_expanded
OFF → compact snapshot
ON → expanded detailed chart

Auto-close timer
When the dropdown opens:
A timer starts (default: 3 minutes)
When the timer finishes:
The dropdown automatically collapses
This keeps dashboards tidy over time.
Hold / pin open (optional)
Another helper:
input_boolean.radial_gauge_hold
When ON:
Auto-close is suppressed
Dropdown stays open until manually closed
Auto-close on navigation (optional)
If Browser Mod is installed:
The dropdown automatically closes when navigating between views
If you don’t use Browser Mod, this automation can be removed safely.
Reusing this pattern
To adapt this for other data types, you only need to change:
Sensor entity IDs
Labels
Colours
Min / max values (if needed)
The dropdown logic and UI behaviour stay exactly the same.

![IMG_5344](https://github.com/user-attachments/assets/962bdb65-7e04-42ed-b6bb-0e6ca3783124)

![IMG_5345](https://github.com/user-attachments/assets/314ce9d2-691d-45f6-ab13-53eaa6274bf0)

