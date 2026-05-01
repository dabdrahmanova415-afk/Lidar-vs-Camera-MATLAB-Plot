# LiDAR vs Camera in Fog — MATLAB Simulation

[![MATLAB](https://img.shields.io/badge/MATLAB-R2023a%2B-blue)](https://www.mathworks.com/products/matlab.html)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Octave](https://img.shields.io/badge/Octave-Compatible-orange)](https://octave.org/)

**Why Tesla can't see a person in fog — a data-driven investigation using real IEEE attenuation coefficients.**

Medium: https://medium.com/@dana_fm/why-tesla-cant-see-a-person-in-fog-i-loaded-10-000-lidar-and-camera-points-into-matlab-4ac4df0475dc

---

## 📌 Overview

This repository contains a complete MATLAB simulation that compares **LiDAR** and **camera** performance in dense fog conditions. The simulation is based on peer-reviewed attenuation coefficients from the paper *"Lidar vs Camera in Adverse Weather"* presented at the **IEEE International Conference on Intelligent Transportation Systems (ITSC 2022)**.

### Key Findings

| Fog Condition | LiDAR Range | Camera Range | Advantage |
|---------------|-------------|--------------|-----------|
| Light fog (50m visibility) | 78 m | 34 m | +44 m (+129%) |
| **Dense fog (20m visibility)** | **42 m** | **16 m** | **+26 m (+163%)** |

At 50 km/h, **LiDAR provides 3.0 seconds** of reaction time vs. only **1.2 seconds** for camera-only systems.

---

## 🚀 What This Repository Contains

- `lidar_vs_camera_fog.m` — Main MATLAB simulation script
- `lidar_vs_camera_app.mlapp` — Interactive App Designer version with slider
- `demo_plot.png` — Example output visualization
- `results.txt` — Sample output from the simulation

---

## 📊 How the Simulation Works

The simulation models a pedestrian standing in fog at distances from 0 to 100 meters. It calculates:

1. **Signal attenuation** using the Koschmieder extinction model
2. **Sensor noise** based on real sensor characteristics
3. **Signal-to-Noise Ratio (SNR)** in decibels
4. **Maximum detection distance** where SNR falls below the ISO 15623 threshold (10 dB)

### The Physics

- **Camera (passive)** — Captures reflected sunlight. Signal decays as `1/distance² × exp(-β×distance)`
- **LiDAR (active)** — Emits laser pulses at 905 nm. Signal decays as `1/distance² × exp(-2×β×distance)`, but the extinction coefficient β is lower for near-infrared wavelengths

**Result:** LiDAR maintains useful signal approximately **twice as far** as cameras in fog.

---

## 🔧 Requirements

- **MATLAB R2019b or newer** (R2023a recommended)
- **Or GNU Octave** (free alternative — most functions work)

No additional toolboxes required. The simulation uses only core MATLAB functions.

---
