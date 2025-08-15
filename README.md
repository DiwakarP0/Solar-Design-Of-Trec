# Multi-Pass-Shell-and-Tube-Heat-Exchanger-and-Solar-Collector

## Overview
This repository contains a complete Python-based simulation and analysis framework for:

1. **Thermal analysis and visualization of a multi-pass shell-and-tube heat exchanger** using hot air and water in a cross-flow arrangement.
2. **Computation and analysis of solar irradiance data** for New Delhi with adjustable parameters, incorporating astronomical position calculations, atmospheric reduction factors, and weather/cloud cover effects.
3. **Integration of meteorological datasets** to enhance computed data with observed temperature and irradiance profiles.
4. **Comprehensive visualization** of results, including temperature distribution, heat flux, GHI (Global Horizontal Irradiance), and seasonal variations.

The project models the thermodynamic behaviour of the heat exchanger system, computes solar input available for thermal energy applications, and combines real and theoretical datasets for year-round analysis.

## Features

### **Heat Exchanger Simulation**
- Models a **multi-pass, shell-and-tube configuration** (4 tube passes, 1 shell pass) with hot air on the shell side and water in the tube side.
- Supports **cross-flow** and **counter-flow** heat transfer calculations.
- Implements **NTU-effectiveness method** with correction factors for multi-pass arrangements.
- Visualizes:
  - Physical schematic of the heat exchanger layout.
  - Flow arrangement and temperature progression.
  - Temperature profile along the exchanger length.
  - Local temperature differences and heat flux distribution.

**Key parameters modelled:**
- Mass flow rate
- Heat duty (Q)
- LMTD (Log-Mean Temperature Difference) with correction factor (F)
- Heat capacity rates and effectiveness

### **Solar Irradiance Modelling**
- Calculates **hourly and daily solar irradiance** based on location (New Delhi, India) using:
  - Declination angle
  - Hour angle
  - Solar altitude angle
  - Solar azimuth angle  
- Incorporates atmospheric attenuation:
  - Default clear-sky reduction factor
  - User-defined factors for hazy or cloudy conditions
  - Mapping from cloud cover data (oktas) to atmospheric reduction
- Ability to handle:
  - Clear-sky modeled data
  - Real IMD dataset integration (when available), with fallback to theoretical estimations

### **Meteorological Data Integration**
- Processes CSV datasets containing:
  - Hourly irradiance values
  - Daily average temperature (`T_mean`)
  - Observed GHI values
- Generates enhanced CSV files with:
  - Declination angle
  - Noon solar altitude and azimuth angles
  - Computed daily GHI (kWh/m²/day)
  - Daily mean irradiance

### **Visualisations**
- **Heat Exchanger Plots:**
  - Cross-section diagrams with tube passes, flow arrows, inlets/outlets
  - Counter-flow temperature plots
  - Heat flux vs position graphs
- **Solar Data Plots:**
  - Annual variation of `Daily I Mean` vs `T_mean`
  - Seasonal irradiance patterns
  - Daily GHI trends

## Software & Libraries Used
- **Python 3**
- **NumPy** – numerical calculations
- **Pandas** – data manipulation and CSV handling
- **Matplotlib** – plotting and schematic diagrams
- **SciPy** – equation solving (for NTU/heat exchanger)
- **datetime** – date/time handling for solar position calculations

## Repository Structure
```
├── heat_exchanger_simulation.py      # Complete exchanger simulation and plotting
├── solar_irradiance_analysis.py      # Solar calculations and weather integration
├── csv_data/                         # Input meteorological datasets
├── generated_results/                # Output enhanced CSVs
├── visualizations/                   # Plotted graphs and figures
├── README.md                         # Project documentation (this file)
```

## How to Run

### **1. Heat Exchanger Analysis**
```bash
python heat_exchanger_simulation.py
```
- Displays exchanger schematic, flow diagram, temperature distribution, and key results summary.

### **2. Solar Irradiance Analysis (Modelled & Observed)**
```bash
python solar_irradiance_analysis.py
```
- Accepts date, time, and atmospheric conditions as inputs.
- Returns simulated/observed irradiance values.

### **3. Generating Enhanced CSV with Angles & GHI**
Place raw CSV (e.g., `solar_irradiance_2024_new_delhi.csv`) in the working directory:
```bash
python solar_data_processing.py
```
- Produces a file like: `solar_irradiance_enhanced_YYYY_new_delhi.csv`.

## Applications
- **Performance prediction** of solar-assisted heat exchanger systems.
- **Feasibility studies** for renewable energy-based water heating.
- **Seasonal optimisation** of heat exchanger parameters.
- **Integration into control systems** for hybrid solar-thermal setups.

## Author
**Diwakar Prajapati**    
