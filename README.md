Is Extreme Heat Changing Faster Than We Realize?

### An Exploratory Analysis of Extreme-Heat Trends Across Selected Grid Cells in Punjab, India (2000–2025)

## 🌍 Overview

Extreme heat is an increasingly important climate concern, affecting public health, agriculture, energy demand, and economic activity. Understanding how daily maximum temperatures vary over time can help identify patterns in extreme-temperature events and support further climate research.

This project uses Python to explore daily maximum temperature data attributed to the **India Meteorological Department (IMD)** across selected grid cells in Punjab, India, covering 2000–2025.

The analysis examines seasonal temperature patterns, annual variations, and changes in the frequency of unusually hot days using percentile-based indicators and statistical trend analysis.

## 🎯 Objectives

- Analyze daily maximum temperature patterns from 2000 to 2025.
- Explore seasonal and monthly temperature variations.
- Identify unusually hot days using monthly 90th-percentile temperature thresholds.
- Examine annual variations in the frequency of extreme-heat days.
- Apply statistical methods to explore potential long-term trends.
- Document data limitations and uncertainty in interpreting climate trends.

## 📊 Dataset

The project uses gridded daily maximum temperature data attributed to the India Meteorological Department (IMD).

| Attribute | Details |
|---|---|
| Data variable | Daily maximum temperature (`tmax`) |
| Period | 2000–2025 |
| Geographic focus | Selected grid cells in Punjab, India |
| Spatial coverage | 6 grid cells in the supplied dataset; 5 contain usable temperature data |
| Temporal resolution | Daily |
| Data format | NetCDF (`.nc`) |
| Units | Degrees Celsius (°C) |
| Source | [India Meteorological Department](https://imdpune.gov.in/) |

The current dataset covers a limited geographical area and should not be interpreted as representing all of Punjab or India.

## 🛠️ Tools and Technologies

- **Python** — data analysis
- **Pandas** — data manipulation and tabular analysis
- **NumPy** — numerical operations
- **Xarray** — handling multidimensional NetCDF climate data
- **Matplotlib** — data visualization
- **SciPy** — statistical analysis
- **Google Colab** — notebook development and execution
- **GitHub** — version control and project documentation

## 🔬 Methodology

The project follows an exploratory data-analysis workflow:

1. **Data loading:** Load the gridded temperature dataset using Xarray.
2. **Data inspection:** Examine the dataset's dimensions, variables, date range, missing values, and spatial coverage.
3. **Data preparation:** Convert the data into a tabular structure for analysis and check temporal completeness.
4. **Exploratory analysis:** Investigate daily, monthly, and annual temperature patterns.
5. **Extreme-heat indicators:** Explore monthly 90th-percentile thresholds to identify unusually hot days.
6. **Trend analysis:** Examine annual changes using statistical methods and visualizations.
7. **Interpretation:** Evaluate observed patterns while accounting for the limited spatial coverage and uncertainty in trend estimates.

The precise threshold reference period and statistical methods used in the final analysis will be documented alongside the corresponding results.

## 📈 Key Areas of Analysis

- Monthly and seasonal temperature patterns
- Annual temperature variations across grid cells
- Identification of unusually hot days
- Annual frequency of extreme-heat days
- Statistical assessment of potential trends
- Data quality, missing observations, and analytical limitations

## 📁 Repository Structure

```text
extreme-heat-trends-india/
│
├── README.md
├── requirements.txt
├── .gitignore
├── extreme_heat_analysis.ipynb
│
└── outputs/
    └── README.md
```

The notebook filename shown above is illustrative; the uploaded file may have a different name.

- `README.md` — project overview, objectives, and methodology
- `requirements.txt` — Python dependencies
- `.gitignore` — files Git should ignore
- `extreme_heat_analysis.ipynb` — interactive analysis notebook
- `outputs/` — visualizations, summary tables, and generated results

## 🚧 Current Status

**Project stage:** Exploratory data analysis and statistical investigation.

The dataset has been inspected, and initial visualizations and preliminary grid-cell trend estimates have been explored. Further analysis is needed to establish robust conclusions about changes in extreme-heat frequency.

The current analysis is limited to five usable grid cells in Punjab, India. Preliminary results should not be interpreted as conclusive evidence of a region-wide trend or accelerating extreme heat.

## ⚠️ Limitations

- The spatial coverage is limited to a small number of grid cells.
- Results may not represent broader regional or national climate patterns.
- Extreme-heat classifications depend on the selected percentile threshold and reference period.
- Statistical trends require careful interpretation, including consideration of sample size, variability, and robustness.
- The analysis identifies statistical patterns but does not independently establish the causes of observed temperature changes.

## 🔮 Future Improvements

- Expand the geographical coverage to include additional regions of India.
- Compare multiple baseline periods for defining extreme heat.
- Investigate heatwave duration and consecutive hot days.
- Assess the sensitivity of results to alternative statistical methods.
- Add clearer maps and spatial comparisons.
- Compare findings with published climate research and relevant official reports.

## 💡 Why This Project Matters

Extreme heat is not just a weather phenomenon; it has implications for livelihoods, infrastructure, agriculture, and economic resilience. Exploring historical temperature records is one way to investigate how heat extremes vary over time and what further evidence is needed to understand their broader significance.

This project demonstrates the use of Python, climate-data handling, exploratory analysis, visualization, and statistical reasoning in an applied environmental data-science problem.

## 👩‍💻 Author

Created as a data-science project exploring historical temperature patterns and extreme-heat indicators in India.

**Feedback and suggestions are welcome.**
