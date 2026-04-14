# Adaptive Image Denoising with Hybrid Filtering and ML Optimization

An interactive Streamlit application for adaptive image denoising that combines
classical image filters, automatic noise profiling, region-aware processing,
machine-learning-based weight prediction, and a self-learning feedback loop.

This project was built as a Digital Image Processing workflow prototype to
compare denoising strategies and visualize how different methods affect image
quality, structure, and edge preservation.

## Highlights

- Detects image noise characteristics before denoising
- Segments the image into smooth, edge, and texture regions
- Applies Gaussian, Median, and Bilateral filtering
- Uses machine learning to predict fusion weights across filters
- Compares global fusion, region-aware fusion, and adaptive denoising outputs
- Tracks PSNR, SSIM, MSE, and Edge Preservation Score (EPS)
- Stores feedback history to support self-learning over time
- Provides a Streamlit dashboard for interactive experimentation

## Pipeline Overview

1. Load a demo image or upload a custom image.
2. Inject configurable Gaussian, Salt-and-Pepper, or Mixed noise.
3. Detect the noise profile from statistical image features.
4. Segment the noisy image into structural regions.
5. Run multiple denoising filters.
6. Predict filter blend weights using a trained regression model.
7. Fuse filter outputs globally and region-wise.
8. Evaluate output quality with image restoration metrics.
9. Save feedback data for future model refinement.

## Project Structure

```text
.
|-- app.py
|-- requirements.txt
|-- test_pipeline.py
|-- feedback_data/
|-- modules/
|   |-- __init__.py
|   |-- filters.py
|   |-- fusion.py
|   |-- metrics.py
|   |-- ml_optimizer.py
|   |-- noise_detection.py
|   |-- region_segmentation.py
|   |-- self_learning.py
|   `-- utils.py
`-- README.md
```

## Main Components

### `app.py`
Streamlit user interface and end-to-end orchestration of the denoising
pipeline.

### `modules/noise_detection.py`
Extracts statistical image features and estimates noise type, intensity, and
distribution pattern.

### `modules/region_segmentation.py`
Separates the image into smooth, edge, and texture regions to support
region-aware denoising.

### `modules/filters.py`
Implements Gaussian, Median, Bilateral, and adaptive region-based denoising.

### `modules/ml_optimizer.py`
Builds synthetic training data, trains machine-learning models, and predicts
filter weights or best-filter recommendations.

### `modules/fusion.py`
Combines filter outputs using global weighted fusion and region-aware fusion.

### `modules/metrics.py`
Calculates restoration metrics such as MSE, PSNR, SSIM, and EPS.

### `modules/self_learning.py`
Stores feedback history and augments future training data using prior runs.

## Requirements

- Python 3.10 or newer
- A virtual environment is recommended
- Dependencies listed in `requirements.txt`

Install dependencies with:

```bash
pip install -r requirements.txt
```

## Run the App

Start the Streamlit interface:

```bash
python -m streamlit run app.py
```

By default, Streamlit opens the app at:

```text
http://localhost:8501
```

## Run the Test Script

To verify that the core modules and pipeline work together:

```bash
python test_pipeline.py
```

## How to Use

1. Launch the Streamlit app.
2. Choose the demo image or upload your own image.
3. Select the noise type and adjust intensity settings.
4. Tune filter parameters if needed.
5. Run the full pipeline from the interface.
6. Review the dashboard sections and compare denoising methods.
7. Download the best denoised output if desired.

## Evaluation Metrics

- `MSE`: Pixel-wise reconstruction error
- `PSNR`: Peak signal-to-noise ratio
- `SSIM`: Structural similarity index
- `EPS`: Edge Preservation Score for structural fidelity

## Use Cases

- Academic Digital Image Processing demonstrations
- Comparing denoising strategies under different noise profiles
- Visualizing region-aware and ML-assisted image restoration
- Exploring self-improving denoising pipelines

## Notes

- The self-learning history file is generated during use and is ignored in Git.
- This repository focuses on experimentation, explainability, and comparative
  analysis rather than production deployment.

## Author

Ankit Kumar

GitHub: [AnkitKumar61](https://github.com/AnkitKumar61)
