# Normalization

Normalize Mediapipe keypoint time series to a shared coordinate and scale.

## Data layout
Place inputs in `data/processed/Output_TimeSeries/` with the existing names.

## Environment
conda env create -f environment.yml
conda activate normalization

## CLI
python scripts/normalize.py \
  --in data/processed/Output_TimeSeries/Cheeseburger_short_body.csv \
  --out results/normalized/Cheeseburger_short_body_norm.csv \
  --method zscore

## Notebook
jupyter lab
# open notebooks/01-normalisation_session.ipynb and run all