# Nairobi EV Charging & Swap Station Site Selection

AHP-weighted multi-criteria suitability analysis identifying optimal locations 
for EV charging (cars) and battery swap stations (motorcycles/tuk-tuks) 
in Nairobi County, Kenya.

## Methodology
- **Data:** OpenStreetMap (roads, POIs, land use, power infrastructure) via HOT Export Tool
- **Criteria:** road proximity, grid/power proximity, fuel station proximity, 
  matatu/bus stop proximity, commercial hub proximity, land use suitability
- **Weighting:** Analytic Hierarchy Process (AHP) with separate pairwise 
  comparison matrices for cars vs. motorcycles (Consistency Ratio < 0.02 for both)
- **Tools:** QGIS (raster processing, distance analysis, weighted overlay), 
  Excel (AHP calculations)

## Results
![Car Suitability Map](Car_Suitability_Map.jpeg)
![Motorcycle Suitability Map](Motorcycle_Suitability_Map.jpeg)

## Key Finding
Suitability is concentrated in Nairobi's already-developed urban core, 
reflecting existing infrastructure density (roads, power, commercial activity). 
This suggests near-term siting priority should focus on optimizing placement 
within these zones, while rural fringe areas would require infrastructure 
investment before becoming viable.

## Files
- `Car_Suitability_Map.jpeg` / `Motorcycle_Suitability_Map.jpeg` — final suitability maps
- `Motocylcle_Swap station AHP.csv` — AHP pairwise comparison matrix and weight calculations
- `Nairobi_EV_Siting.qgz` — full QGIS project file

  ## How to Reproduce
1. Export OSM data for your study area via HOT Export Tool (roads, POIs, land use, power)
2. Clip layers to study area boundary in QGIS
3. Generate distance-to-feature rasters using Proximity (Raster Distance)
4. Normalize each raster to a 0–1 scale
5. Build AHP pairwise comparison matrices in Excel to derive criteria weights 
   (verify Consistency Ratio < 0.10)
6. Combine normalized rasters using Raster Calculator with AHP weights
7. Reclassify and style the final suitability surface
