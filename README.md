# StormSurge

**An extreme-event benchmark and physics-constrained ML framework for 
thermospheric density forecasting during geomagnetic storms.**

Built for the NASA × Hack Club Stardance Challenge 2026.

---

## The Problem

When extreme geomagnetic storms hit Earth, the thermosphere heats up and 
expands — satellite drag can spike 10× within hours. The May 2024 Gannon 
storm (the strongest in over 20 years) caused the largest satellite mass 
migration in history and severely degraded collision avoidance systems 
worldwide for multiple days.

Existing empirical and ML models show significantly degraded performance 
under extreme storm conditions. The core issue: models trained on quiet 
and moderate storm data cannot reliably extrapolate to the rare but 
catastrophic tail of the distribution.

**StormSurge addresses this in three parts:**

1. **Benchmark** — A rigorous held-out evaluation suite using the May 2024 
   Gannon storm (G5) and October 2024 storm (G4) as extreme test cases. 
   No published focused benchmark exists for these two events combined.

2. **Baselines** — Systematic comparison of persistence, NRLMSIS-2.0, 
   JB2008, and STORM-AI-style ML models against the benchmark.

3. **Model** — A transformer-based forecaster with physics-inspired 
   constraints, storm-intensity weighted training, and calibrated 
   uncertainty quantification.

If the model only improves modestly, the benchmark is still a standalone 
research contribution.

---

## Why This Matters

- 9,000+ satellites currently operate in LEO
- We are in the most active phase of Solar Cycle 25
- Accurate drag forecasting during extreme storms is critical for 
  collision avoidance, orbital maintenance, and mission planning
- NASA, ESA, and commercial operators have no reliable short-term 
  density forecast for G4–G5 events

---

## Contributions

- First focused held-out benchmark using Gannon 2024 + October 2024 
  as combined extreme-event test set
- Physics-inspired training constraints (realistic lag, recovery 
  dynamics, NRLMSIS-2.0 as prior feature) to improve extrapolation
- Storm-intensity weighted training strategy targeting G4–G5 events
- Calibrated uncertainty output for operational use
- Open-source, reproducible, documented for the research community

---

## Data Sources

| Source | Variables | Access |
|--------|-----------|--------|
| STORM-AI devkit (MIT ARCLab) | Density + space weather, pre-cleaned | github.com/ARCLab-MIT/STORM-AI-devkit-2025 |
| NASA OMNI | Solar wind, IMF Bz | omniweb.gsfc.nasa.gov |
| NOAA SWPC | Kp, Dst, AE indices | swpc.noaa.gov |
| ESA Swarm A/B/C | In-situ thermospheric density | earth.esa.int |
| NRLMSIS-2.0 | Empirical model prior | via `nrlmsise00` Python package |

---

## Project Structure
