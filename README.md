# 🏃‍♀️ Modeling Elite Marathon Performance with Generalized Extreme Value Theory

This repository contains the data scraping, modeling code, and exploratory analysis for my thesis:  
**“Generalized Extreme Value Theorem in Modeling of Top Marathon Performances by Gender and Nationality”**  

---

## 📌 Project Overview

Elite marathon running has undergone a radical transformation in the past four decades — not just in performance outcomes, but in **who** competes and **why**. Once an amateur pursuit, the marathon became a global career path, catalyzed by the introduction of prize money, professional sponsorships, and national recognition.

This project uses **Extreme Value Theory (EVT)** to model the *right tail* of marathon performance — the elite outliers who not only win races, but redefine the limits of human potential. Using top 100 marathon performances from 1981 to 2023, it examines trends across **gender** and **nationality**, with a particular focus on the rise of African nations.

---

## 💡 Motivation & Broader Context

The introduction of **economic incentives** in professional road racing marked a turning point in the sport. For athletes — especially those from African nations — distance running became a rare and viable pathway to:

- 🏅 Life-changing **financial rewards**
- 🌍 **Citizenship and international competition** opportunities
- 🇰🇪 **National pride** and legacy
- 🏃‍♂️ Infrastructure for future generations

These incentives didn’t just expand the talent pool — they changed the **trajectory** of performance itself.

This thesis investigates how these structural shifts fueled a new era of excellence, using EVT to analyze the evolution of top-tier performances. EVT is uniquely suited to this task, offering tools to model **the extremes**, where singular acts of greatness set a new bar for all who follow.

Today, factors like **performance footwear**, **social media exposure**, and **broader international access** continue to shape the sport — but the heart of this work is the **economics of excellence**, and how opportunity fuels performance.

---

## 🔬 Methods Summary

### 🗂 Data Collection

- **Source**: [World Athletics](https://worldathletics.org/) toplists
- **Years Covered**: 1981–2023
- **Athletes**: Top 100 male and female marathon performances per year
- **Scraping Tool**: `rvest` in R
- **Cleaning**:
  - Times converted to seconds
  - DOB cleaned to compute athlete age
  - Region tagging: African vs. non-African athletes

### 📊 Modeling Approach

- Modeled **top 10** finishers per group/year using:
  - Custom-written **GEV likelihood function**
  - Natural splines via `ns()` (R's `splines` package)
- Hand-validated GEV function against `fevd()` from `extRemes`
- Model selection based on:
  - AIC, AICc, BIC
  - 5-fold cross-validation

---

## 📈 Key Findings

- 📉 **African male athletes** have consistently faster top performances, but the *rate* of improvement over time is similar to other groups — suggesting sustained rather than explosive dominance
- 📊 **Spline models** revealed near-linear improvement, indicating no major regime shifts — just steady progression
- 🧮 In early years, **censoring in women’s data** (due to 2:35 time cutoff) required specialized GEV extensions
- 🌍 Differences in performance distributions reflect both **biological potential** and **structural access to opportunity**

---

## 📁 Repository Structure

```bash
.
├── thesis_analysis.Rmd               # Full scraping and modeling workflow
├── /data                             # Raw and cleaned data (not public)
├── /scripts                          # GEV estimation, spline model setup
├── /figures                          # Plots used in thesis (e.g., spline fits, spread)
└── README.md                         # This file

📚 Academic Context
This work builds upon and extends foundational research in:

Extreme Value Theory — Coles (2001), Smith (1988), Robinson & Tawn (1995)

Athletic records modeling — Einmahl et al. (2008)

Spline regression for time series — Huang & Shen (2004), Perperoglou et al. (2019)

Economic sociology of sport — Njororai Simiyu (2012)

It was developed as part of my undergraduate honors thesis in Statistics and Analytics.

🧠 About the Author: Why Marathon Records?
This project was deeply personal. I was on the course during the 2023 Chicago Marathon when Kelvin Kiptum broke the world record, running faster than any human in history. I was at mile 16, far, far behind, when the crowd roared. I got chills realizing that I was quite literally following the same path where history had just been made. That moment sparked something in me, a desire to explore how performances like that happen, and what makes greatness possible.

This thesis is my attempt to answer those questions — with data, rigor, and heart.
