# Solar-Panel-Technology-Performance-Analysis


## 📌 Overview
This project compares the performance of various solar panel technologies (monocrystalline, polycrystalline, and thin-film) under different environmental conditions using simulation-based analysis. The goal is to identify the most efficient and cost-effective technology for a given geographic region.

---

## 🏠 Assumptions & Setup
```python
# Panel Types and Efficiencies
panel_types = {
    "Monocrystalline": 0.20,
    "Polycrystalline": 0.17,
    "Thin-film": 0.13
}

# Site Conditions (e.g., Chennai, India)
irradiance = 5.5        # kWh/m2/day
temperature_coeff = -0.004  # % loss per °C above 25°C
ambient_temp = 35        # Average temperature
panel_area = 1.6         # sq.m
```

---

## 📊 Technology Comparison Simulation
```python
import pandas as pd

results = []

for panel, efficiency in panel_types.items():
    temp_loss = (ambient_temp - 25) * abs(temperature_coeff)
    effective_efficiency = efficiency * (1 - temp_loss)
    daily_output = irradiance * panel_area * effective_efficiency
    monthly_output = daily_output * 30
    annual_output = monthly_output * 12
    results.append([panel, round(effective_efficiency * 100, 2), round(annual_output, 2)])

# Display Table
comparison_df = pd.DataFrame(results, columns=["Panel Type", "Effective Efficiency (%)", "Annual Energy Output (kWh)"])
print(comparison_df.to_string(index=False))
```

---

## 📄 Deliverables
- Efficiency-based comparison of panel technologies
- Annual energy yield estimation
- Climate-adjusted performance analysis
- Output table for stakeholder decision-making

---

## ✅ Tools Used
- Python (pandas, math)
- Location-based climate data
- Simulation logic for temperature correction
- Optional extension using PVsyst or PV*SOL
