# MediaPipe Keypoints Normalization

Normalize MediaPipe keypoint time series to a shared coordinate system and scale for cross-participant comparability.

## 🔬 Research Context

This module is part of a larger research workflow for gesture and motion analysis. Normalization ensures that trajectories are comparable across recordings with different resolutions, camera setups, and subject sizes.

## 🎯 What This Project Does

This module covers:

1. **Input Loading**: Read body and hand keypoint CSVs exported from upstream steps
2. **Coordinate Normalization**: Map pixel coordinates to normalized coordinates (e.g., width/height)
3. **Scale Normalization**: Standardize amplitudes across participants/sessions
4. **Export**: Write normalized time series to disk for downstream analysis

## 📊 Normalization Process

The notebook follows a simple workflow:

1. **Begin with Cleaned Data**: Use smoothed/cleaned CSVs from `Smoothing` or raw if needed
2. **Inspect Distributions**: Check ranges per-axis and per-keypoint
3. **Apply Normalization**: Choose and apply a normalization strategy
4. **Validate**: Visually and quantitatively verify effects
5. **Save**: Export normalized CSVs

## 🔧 Normalization Methods

Implemented in the notebook (adjust as needed in `Normalisation.ipynb`):

- **Min–Max scaling**: Map to [0, 1] per axis/per keypoint
- **Z-score standardization**: Mean 0, std 1 per axis/per keypoint
- **Reference-based scaling**: Normalize by body reference (e.g., shoulder width) when available

## 📁 Project Structure

```
Normalization/
├── README.md
├── environment.yml
├── notebooks/
│   └── Normalisation.ipynb
├── data/
│   └── processed/
│       └── Output_TimeSeries/       # Input CSVs (body/hands)
├── results/
│   └── normalized/                  # Output normalized CSVs
└── src/
    └── normalization/
        └── __init__.py
```

## 🚀 Quick Start

### Prerequisites

```bash
conda env create -f environment.yml
conda activate normalization
```

### Run the Interactive Notebook

```bash
jupyter lab
# Open notebooks/Normalisation.ipynb
```

### Basic Usage

1. Place input CSVs in `data/processed/Output_TimeSeries/`
2. Choose normalization method(s) in the notebook
3. Run the cells to generate normalized outputs
4. Find outputs in `results/normalized/`

## 📈 Data Format

### Input
- **CSV files**: Time series for body and/or hands (columns for each landmark coordinate)

### Output
- **CSV files**: Same structure as input, with normalized coordinate values

## 🔗 Related Projects

- `../Smoothing/` – optional preprocessing before normalization
- `../MediaPipe_keypoints_extraction/` – raw keypoint extraction

## 📖 References

- Feature scaling in time series analysis and gesture research literature
