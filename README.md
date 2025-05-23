# Nestergy

Want to supply your home with renewable electricity and heat 24/7/365?

Nestergy helps you take an informed decision based on:

- your location,
- your budget, and
- the expanding sea of technological possibilities available right now

🦾🫀🐍

# Table of Contents

<!-- START doctoc -->
<!-- END doctoc -->

- [Overview](#overview)
- [Key Features (MVP)](#key-features-mvp)
  - [Location-Based Climate Data](#location-based-climate-data)
  - [Solar Recommendations](#solar-recommendations)
  - [Energy Storage](#energy-storage)
  - [Agent](#agent)
    - [Scrape Data](#scrape-data)
    - [Update Recommendations](#update-recommendations)
    - [Example Impact](#example-impact)
    - [Implementation Plan](#implementation-plan)
- [Key Features (extension plans)](#key-features-extension-plans)
  - [Location-Based Climate Data (extended)](#location-based-climate-data-extended)
  - [Budget Calculator](#budget-calculator)
  - [Advanced Cost Estimation](#advanced-cost-estimation)
  - [Energy Savings Simulator](#energy-savings-simulator)
  - [Weather and Climate Integration](#weather-and-climate-integration)
  - [Vendor Comparison](#vendor-comparison)
  - [Carbon Footprint Tracker](#carbon-footprint-tracker)
  - [Community Features](#community-features)
  - [Mobile App Development](#mobile-app-development)
  - [Time Series (extension)](#time-series-extension)
    - [Cost Prediction](#cost-prediction)
    - [Technology Lifetime](#technology-lifetime)
    - [Implementation Plan](#implementation-plan-1)
- [Data Sources — MVP: U.S. Solar + Battery](#data-sources--mvp-us-solar--battery)
  - [Minimum Viable Product: U.S. Solar PV + Li-ion Batteries](#minimum-viable-product-us-solar-pv--li-ion-batteries)
  - [Extensions: Global Reach & Tech Diversity](#extensions-global-reach--tech-diversity)
    - [Expand Geographically](#expand-geographically)
    - [Expand Technologies](#expand-technologies)
- [Getting Started](#getting-started)
- [License](#license)
  - [Authors](#authors)

# Overview

Nestergy is a web-based platform designed to guide you in selecting renewable
energy and storage solutions.

Based on your location (latitude and longitude), Nestergy retrieves climate data
like temperature range and sunshine hours to provide tailored recommendations on
how to supply your home with renewable energy and storage.

This platform aims to streamline your decision-making process, considering
factors like energy needs, budget constraints, and local climate conditions.

# Key Features (MVP)

Since this is an ambitious project touching on various technical challenges and
ongoing research, the project is starting off with an MVP, focusing on solar
power in the USA using only commercially available litium-ion batteries. The MVP
will include:

## Location-Based Climate Data:

Based on user location input (latitude, longitude), fetch corresponding climate
data (daily min-max across entire year) based on reference period (e.g. 3
years):

- temperature (C)
- solar radiation (W/m²)
- sunshine (h/d)

# TODO

user story

- I want to supply this location for x people in timeframe starting in y years
  until z years lifetime

model idea

- what is best design of house to give me
- large area to produce
- energy efficiency, passive heating and cooling
- most profit to sell electricity to grid
- architecture using ML --> real contribution, create design . least consumption
  and max production
- diffusion model to create images

automation

an agent asking user in chat

LLM model searching DB

updating DB

agent on steroids

- optimized and fine-tuned by a scientist (myself)

- use mcp server to search the web (simple, no model coding)
  - don't need processing power
  - create own agent using own time series
  - use case: time series forecast of non-deterministic input
    - scenarios for money, foreign exchange rates, inflation
- RAGs (medium effort, =coding part)
  - keep updating db
  - store in mongo db, vector db, embed new papers / commercial available
  - place most cost-efficient solution for each energy source into db
  - get closest vectors from database (dot-product)
  - give most similar vectors to LLM
  - LLM mixing to create human-readable output
    - manual implementation of search-the-web
- fine-tune model (expensive and complex, retraining every month cost effective)
  - need virtual machines
    - need vertex AI
    - compute engine

## property data

- Roof Angle (in degrees) as a user input allows Nestergy to account for the
  tilt of the roof, which affects solar panel efficiency. The angle influences
  how directly sunlight hits the panels, impacting energy yield (e.g., optimal
  angles vary by latitude for maximum solar exposure). Roof Area: Including roof
  area (in square meters or square feet) enables the platform to estimate the
  maximum number of solar panels that can be installed, which is critical for
  calculating potential energy generation and system costs.

## Solar Recommendations:

Suggests solar panel solutions based on climate data and user preferences.

## Energy Storage:

Suggest eletric storage capacity (kWh) per person to cover lowest production
period for user input location and get associated cost.

## Agent

To keep Nestergy up to date with developments in renewable energy and storage
solutions, an agent will be developed.

This agend will continuously update the platform’s technology database with the
latest state-of-the-art advancements in renewable electricity, heat generation,
and energy storage. This agent will:

### Scrape Data:

Automatically gather data from trusted sources (e.g., industry reports,
renewable energy journals, manufacturer websites) on new solar panels, heat
pumps, and energy storage systems (e.g., lithium-ion, solid-state batteries).

### Update Recommendations:

Integrate the latest technologies into Nestergy’s recommendation engine,
ensuring users receive suggestions based on cutting-edge options.

### Example Impact:

If a new high-efficiency solar panel (e.g., 25% efficiency vs. 20% for current
models) enters the market in 2026, the agent will update Nestergy’s database,
allowing users to benefit from improved recommendations.

### Implementation Plan:

- Use web scraping to collect data.
- Store technology data in a structured database.
- Develop an update pipeline to refresh recommendations weekly or monthly.

# Key Features (extension plans)

Nestergy can be expanded with the following features to enhance its
capabilities:

### Location-Based Climate Data (extended):

- access to running water for hydropower
- wind speed for wind energy
- geothermal suitability for combined heat and power
- access to biomass for combined heat and power

### Budget Calculator:

Enter your budget to see which technologies fit your financial constraints.

### Advanced Cost Estimation:

Integrate detailed cost breakdowns, including installation, maintenance, and
potential government subsidies or tax incentives for renewable energy adoption.

### Energy Savings Simulator:

Add a tool to simulate long-term energy savings and return on investment (ROI)
based on the chosen technology and local energy prices.

### Weather and Climate Integration:

Incorporate real-time weather data and climate patterns to provide more accurate
recommendations (e.g., solar panel efficiency based on sunlight hours in your
area).

### Vendor Comparison:

Partner with renewable energy vendors to allow users to compare quotes and
services directly within the platform.

### Carbon Footprint Tracker:

Add a feature to calculate and track the reduction in carbon footprint achieved
by switching to renewable energy solutions.

### Community Features:

Introduce a community section where users can share experiences, tips, and
success stories about their renewable energy setups.

### Mobile App Development:

Create a mobile app version of Nestergy for on-the-go access to recommendations
and tools.

## Time Series (extension)

To enhance Nestergy’s utility for long-term building projects, we will implement
a time series model to predict the cost of known renewable energy technologies
as a baseline scenario, tailored to projects with a specific future completion
date. Additionally, this model will estimate the expected lifetime of the chosen
technology mix. This feature will:

### Cost Prediction:

Use historical cost data for renewables (e.g., solar panels, batteries) to train
a time series model (ARIMA or LSTM).

Predict future costs based on trends, inflation, and market adoption (e.g.,
solar panel costs have historically dropped ~10% annually due to technological
advances).

#### Example:

For a project completing in 2030, predict the cost of a 5 kW solar system,
considering expected price declines.

### Technology Lifetime:

Estimate the lifespan of the recommended technology mix based on manufacturer
data, environmental conditions (e.g., temperature, humidity from NASA POWER),
and usage patterns.

#### Example:

A solar panel in a high-radiation, low-humidity area (e.g., Texas) might last 30
years, while the same panel in a cold, snowy climate (e.g., Alaska) might last
25 years due to thermal stress.

### Implementation Plan:

- Collect historical cost data from public sources and clean it for modeling.
- Use Python libraries like statsmodels for time series forecasting.
- Integrate environmental data (NASA POWER’s T2M_RANGE) to adjust lifetime
  estimates.
- Display predictions in the web interface: “Expected cost in 2030: $5,000 for a
  5 kW system; Estimated lifetime: 28 years.”

# 📊 Data Sources — MVP: U.S. Solar + Battery

Nestergy uses climate data from the NASA POWER Project, providing reliable,
model-derived meteorological and solar radiation data for renewable energy
applications.

## Minimum Viable Product: U.S. Solar PV + Li-ion Batteries

- **Solar Irradiance (U.S.)** Hourly/daily solar potential by ZIP code →
  [NREL NSRDB (National Solar Radiation Database)](https://nsrdb.nrel.gov/) →
  [PVWatts Calculator (API)](https://developer.nrel.gov/docs/solar/pvwatts/v6/)

- **Residential Solar PV System Costs & Efficiency** CAPEX, efficiency curves,
  system lifetimes → [NREL Annual Technology Baseline](https://atb.nrel.gov/) →
  [SEIA Solar Market Insight](https://www.seia.org/research-resources/solar-market-insight-report)

- **Li-ion Battery Storage Specs** Depth of discharge, efficiency, degradation,
  lifespan →
  [NREL Energy Storage Database](https://www.nrel.gov/grid/energy-storage.html)
  →
  [DOE Energy Storage Grand Challenge](https://www.energy.gov/energy-storage-grand-challenge)

- **U.S. Electricity Prices & Net Metering Rules** Retail rates and
  state-by-state compensation schemes →
  [U.S. Energy Information Administration (EIA)](https://www.eia.gov/electricity/data/)
  → [DSIRE USA Policy Database](https://www.dsireusa.org/)

- **State-Level Solar Incentives & Tax Credits** →
  [DSIRE Incentives Search Tool](https://www.dsireusa.org/)

---

## 🚀 Extensions: Global Reach & Tech Diversity

### 🌍 Expand Geographically

- **Solar (Global)** → [Global Solar Atlas](https://globalsolaratlas.info/)
- **Battery & Storage (Global)** →
  [IRENA Storage Cost Reports](https://www.irena.org/Statistics/View-Data-by-Topic/Costs)
- **Electricity Price by Country** →
  [IEA Energy Prices](https://www.iea.org/data-and-statistics)

### ♻️ Expand Technologies

- **Wind** → [Global Wind Atlas](https://globalwindatlas.info/)
- **Biomass/Biogas** → [IEA Bioenergy](https://www.ieabioenergy.com/)
- **Heat Pumps / Solar Thermal** →
  [EHPA Stats](https://www.ehpa.org/market-data/)
- **Hydro / Microgrid Tools** →
  [Open Energy Platform](https://openenergy-platform.org/)

# Getting Started

(To be added: installation instructions, usage guide, etc., once the MVP is
developed.)

# License

Licensed under the MIT License to encourage collaboration and adoption. Feel
free to use, modify, and distribute! and add yourself to the authors list along
with your contributions 🦾🫀🐍

## Authors:

- FadriPestalozzi (GitHub)

# 🐣 Easter Egg: Hatching "Nestergy"

<details>
<summary>Curious about how Nestergy got its name? Click to find out! 🌟</summary>

- Nestergy was born in Barcelona on the sunny Thursday morning of May 22, 2025.
- At 08:22 AM CEST, the mutual prompts between a human and a machine to explore
  ways of expressing a cozy, warm home, embraced by the pulsating power of
  renewable energy, culminated in the name "Nestergy".
- The machine, aka one of the many incarnations of
  [Ada Lovelace](https://en.wikipedia.org/wiki/Ada_Lovelace), started off with
  the human requirements, combining and re-combining them in impossible ways.
- EnerSpec.AI felt too cold.
- EnerNest already included the warmth of a "nest"
- Wanting to hint at heat, electricity, and synergy, we continued playing with
  names like LumaNest, ThermaNest, and VoltNest
- ... until we hatched-out Nestergy — a perfect blend of _nest_ (for warmth),
  _synergy_ (for combining heat and power), and _energy_ (for renewable
  solutions).
- It’s memorable, emotionally resonant, and tech-forward
- a name that captures the heart and innovation of this project 🦾🫀🐍

</details>
