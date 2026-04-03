# CCRtools

An iOS application for closed-circuit rebreather (CCR) divers. CCRtools helps you prepare for dives safely with checklists, gas blending calculations, O₂ sensor tracking, and standard diving calculators.

---

## Features Overview

| Tab | Purpose |
|-----|---------|
| **Checklist** | Run pre/post-dive checklists with timers, value inputs, and text-to-speech |
| **Sensor Log** | Record O₂ sensor millivolt readings and track linearity over time |
| **Tools** | Calculate MOD, EAD, END, Best Mix, and gas density |
| **Blending** | Plan gas fills using the Ideal Gas Law or Van der Waals equation |

---

## Checklist

The Checklist tab lets you manage and run structured dive checklists. The app ships with a Demo list illustrating the features and a KISS Sidewinder pre-dive checklist; additional checklists can be downloaded, imported, or shared.

### Checklist Library

- **Download** — fetches checklists from the CCRtools server (this github repository - requires Internet)
- **Import** — opens a file picker to load a `.json` checklist file
- **Share** — exports a checklist as a JSON file you can send to other divers
- **New** — creates a blank checklist you can edit
- Swipe left on a checklist row to access **Edit**, **Share**, and **Delete**

### Running a Checklist

Tap a checklist to open it. The checklist progresses section by section (e.g., *Computer*, *Scrubbers*, *Negative test*). Each section can contain:

- **Check items** — simple checkboxes; tap to mark done
- **Value items** — numeric input fields, e.g., sensor millivolt readings; values outside the expected range are highlighted in red
- **Timer items** — countdown timers; start the timer and the item completes automatically

After the last section a summary screen is shown. If the checklist is linked to the Sensor Log, the entered values are saved as a new sensor reading automatically.

### Text-to-Speech

Tap the **speaker icon** in the checklist toolbar to enable hands-free mode. The app reads each checklist item aloud using the system TTS engine. The currently spoken item is highlighted in blue. The language is determined by the system locale (English or German) or overridden per checklist.

---

## Sensor Log

The Sensor Log tracks O₂ sensor millivolt readings over time to monitor sensor health. The KISS Sidewinder supports up to five O₂ sensors.

### Recording Readings

Readings are created automatically when you complete a linked checklist. Each reading stores:

- Ambient mV and O₂ mV for each sensor (up to 5)
- Battery voltage (2 channels)
- Scrubber time remaining

**Linearity** is calculated per sensor:

```
Linearity = (O₂ mV / (Ambient mV × 4.77)) × 100 %
```

A healthy sensor reads close to 100 %.

### Sensor Log Table

The main view shows a table with one row per dive, sorted newest first. Columns display linearity percentages for each sensor. Rows with sensor replacements are marked.

- **Sensor change** buttons record which sensors were swapped
- Swipe left on a row to **delete** it
- Tap **Export** to save all readings as a CSV file

### Sensor Chart

Tap the chart icon to open a trend view showing linearity over time as a line chart. Vertical dashed lines mark sensor replacement dates. The y-axis covers 90–105 % linearity.

---

## Tools

The Tools tab provides stateless diving calculations. Enter a depth and gas mix, and the results update instantly.

### Inputs

| Field | Description |
|-------|-------------|
| **Depth** | Target depth in metres (1–100 m) |
| **Gas mix** | Choose a preset (Air, 21/35, 18/45, 15/55, 10/70, 7/75) or enter O₂ % and He % manually |
| **pO₂** | Partial pressure of oxygen target (default 1.2 bar for Best Mix) |

### Calculated Results

| Calculation | Description |
|-------------|-------------|
| **Best Mix** | Optimal O₂ fraction for the given depth and pO₂ limit |
| **MOD** | Maximum Operating Depth for the current mix at 1.4 and 1.6 bar pO₂ |
| **EAD** | Equivalent Air Depth — narcotic equivalent assuming O₂ is non-narcotic |
| **END** | Equivalent Narcotic Depth — full narcosis model including O₂ |
| **Gas Density** | Density of the breathing gas in g/L at depth |

Gas density above 5.0 g/L is highlighted as a warning (increased breathing resistance).

---

## Gas Blending

The Blending tab calculates how much O₂, helium, and air to add to a tank to reach a target mix. It supports both the Ideal Gas Law and the more accurate Van der Waals equation.

### Inputs

| Field | Description |
|-------|-------------|
| **Start mix** | Current gas in the tank (O₂ % / He %) |
| **Start pressure** | Current pressure in the tank (bar) |
| **Target mix** | Desired final gas mix (O₂ % / He %) |
| **Target pressure** | Desired final pressure (bar) |
| **Filling order** | O₂ → He → Air  or  He → O₂ → Air |
| **Method** | Ideal Gas or Van der Waals |
| **Temperature** | Tank temperature in °C (Van der Waals only, default 20 °C) |
| **Tank volume** | Tank volume in litres (Van der Waals only, default 12 L) |

### Results

The result panel shows the pressure to add for each gas in sequence:

1. First gas (O₂ or He, depending on filling order)
2. Second gas (He or O₂)
3. Air top-up

It also shows the MOD of the final mix at 1.4 bar and 1.6 bar pO₂.

### Ideal Gas vs. Van der Waals

Tap **Compare** to see a side-by-side table of results from both methods. Differences are highlighted in orange. The Van der Waals method accounts for intermolecular forces and molecular volume and is more accurate at high pressures. The Z factor (compressibility) is shown to indicate how much the gas deviates from ideal behaviour.

### Safety Warnings

The app displays warnings for:

- **Hypoxic mix** — O₂ below 16 %
- **Hyperoxic mix** — O₂ above 40 %
- **Pure oxygen** — 100 % O₂

> **Important**: Always verify gas mixes with a calibrated oxygen analyser before diving. This app is a planning aid only and does not replace proper gas analysis equipment or training.

---

## Onboarding

On first launch (and after major updates) the app shows a brief onboarding flow with annotated screenshots explaining each section. It can be revisited by deleting and reinstalling the app.

---

## Requirements

- iOS 17 or later
- iPhone (optimised for iPhone; iPad compatible)

---


## Disclaimer

CCRtools is a dive planning and logging tool. All calculations are provided for informational purposes. Always follow your training, verify gas mixes independently, and dive within your certification limits.
