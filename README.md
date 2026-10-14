# extreme-heat-trends-india
from scipy.stats import theilslopes, kendalltau

# 1. Define the reference and analysis periods
reference = ds.sel(time=slice("2000-01-01", "2014-12-31"))
analysis = ds.sel(time=slice("2015-01-01", "2025-12-31"))

# 2. Calculate monthly 90th-percentile thresholds
threshold = reference["tmax"].groupby("time.month").quantile(
    0.90, dim="time", skipna=True
)

# 3. Match each analysis day to its calendar-month threshold
daily_threshold = threshold.sel(month=analysis["time"].dt.month)

# 4. Count exceedance days, preserving missing observations
valid = analysis["tmax"].notnull()
exceedances = (analysis["tmax"] > daily_threshold).where(valid)

annual_counts = exceedances.groupby("time.year").sum(
    dim="time", skipna=True
)

# Exclude grid cells with no valid observations
has_data = valid.any(dim="time")
annual_counts = annual_counts.where(has_data)

results = (
    annual_counts.to_dataframe(name="extreme_heat_days")
    .reset_index()
    .dropna(subset=["extreme_heat_days"])
)

# 5. Estimate trends using Theil-Sen slopes and Kendall's tau
trend_results = []

for (lat, lon), group in results.groupby(["lat", "lon"]):
    group = group.sort_values("year")
    x = group["year"].to_numpy()
    y = group["extreme_heat_days"].to_numpy()

    if len(y) >= 5 and np.unique(y).size > 1:
        slope, intercept, low, high = theilslopes(y, x)
        tau, p_value = kendalltau(x, y)

        trend_results.append({
            "latitude": lat,
            "longitude": lon,
            "sen_slope_days_per_year": slope,
            "slope_95ci_low": low,
            "slope_95ci_high": high,
            "kendall_tau": tau,
            "kendall_p_value": p_value
        })

trend_table = pd.DataFrame(trend_results)

# 6. Plot annual counts for 2015–2025
plt.figure(figsize=(12, 6))

for (lat, lon), group in results.groupby(["lat", "lon"]):
    group = group.sort_values("year")
    plt.plot(
        group["year"],
        group["extreme_heat_days"],
        marker="o",
        linewidth=1.2,
        label=f"{lat}°N, {lon}°E"
    )

plt.title("Extreme-Heat Days: Evaluation Period 2015–2025")
plt.xlabel("Year")
plt.ylabel("Days Above Reference-Period Threshold")
plt.legend(bbox_to_anchor=(1.02, 1), loc="upper left")
plt.grid(alpha=0.3)
plt.tight_layout()
plt.show()

print("Exploratory trend results:")
display(trend_table.round(4))

# 7. Save outputs
results.to_csv("extreme_heat_days_2015_2025.csv", index=False)
trend_table.to_csv("extreme_heat_trend_results.csv", index=False)

print("Saved both CSV files.")
