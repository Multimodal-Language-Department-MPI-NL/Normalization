Normalize MediaPipe keypoint time series to a shared coordinate system and scale for cross-participant comparability.

![Keypoint normalization demo](src/normalization/keypoint_normalization.gif)

> Illustration: Example of coordinate and scale normalization applied to wrist trajectories relative to body references.

## 🔬 Research Context

This module shows how to normalize the size and position of motion tracking data across files. Normalization ensures that the data for all files is on the same scale so that you can compare movement trajectories across files with different resolutions, camera setups, and participant sizes.

## 🎯 What This Project Does

This module covers:

1. **Input Loading**: Read body and hand keypoint CSVs exported from upstream steps
2. **Coordinate Normalization**: Map pixel coordinates to normalized coordinates (e.g., width/height)
3. **Scale Normalization**: Standardize amplitudes across participants/sessions
4. **Export**: Write normalized time series to disk for downstream analysis

## 📊 Smoothing Process

The notebook follows a simple workflow:

1. **Begin with Cleaned Data**: Use smoothed/cleaned CSVs from `Smoothing` or raw if needed
2. **Inspect Distributions**: Check ranges per-axis and per-keypoint
3. **Apply Normalization**: Choose and apply a normalization strategy
4. **Validate**: Visually and quantitatively verify effects
5. **Save**: Export normalized CSVs

## 🔧 Smoothing Techniques

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


## 📈 Data Format

### Input
- **CSV files**: Time series for body and/or hands (columns for each landmark coordinate)

### Output
- **CSV files**: Same structure as input, with normalized coordinate values

## 🔗 Related Projects

- `https://github.com/Multimodal-Language-Department-MPI-NL/Smoothing` – optional preprocessing before normalization
- `https://github.com/Multimodal-Language-Department-MPI-NL/MediaPipe_keypoints_extraction` – raw keypoint extraction

## 📖 References


