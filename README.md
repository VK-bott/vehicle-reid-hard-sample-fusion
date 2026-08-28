# Vehicle Re-Identification with Hard-Sample Mining and Dual-Model Fusion

A PyTorch-based vehicle re-identification project that improves image-retrieval performance by identifying difficult queries, applying targeted retraining, and combining a baseline model with a specialised model.

The project was evaluated on the VeRI-776 benchmark using mean Average Precision (mAP) and per-query Average Precision (AP). The proposed workflow achieved an approximately 3% mAP improvement over the baseline experiment.

## Project Overview

Vehicle re-identification aims to retrieve images of the same vehicle across different cameras, viewpoints, lighting conditions, and backgrounds. These variations make some query images considerably more difficult than others.

This project implements a performance-improvement workflow consisting of:

1. Training and evaluating a baseline vehicle re-identification model.
2. Calculating Average Precision for individual query images.
3. Identifying low-AP hard-query samples.
4. Building a specialised training subset for difficult or low-light images.
5. Retraining and tuning a focused model.
6. Combining the baseline and specialised models through a dual-model inference strategy.
7. Comparing the resulting mAP and retrieval performance with the baseline.

## Key Features

- Vehicle re-identification using PyTorch
- Training and evaluation on the VeRI-776 benchmark
- Per-query Average Precision analysis
- Automated identification of low-performing queries
- Hard-sample and low-light image selection
- Targeted model retraining
- Configurable experiments using YAML files
- Dual-model fusion and performance comparison
- Visualisation of query-level AP distributions

## Repository Structure

```text
vehicle-reid-hard-sample-fusion/
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
├── configs/
│   ├── baseline.yaml
│   └── focused_model.yaml
├── notebooks/
│   └── experiment_analysis.ipynb
├── src/
│   ├── train.py
│   ├── evaluate.py
│   ├── hard_sample_mining.py
│   └── dual_model_inference.py
├── results/
│   ├── ap_bin_statistics.png
│   ├── baseline_per_query_ap.csv
│   └── dual_model_per_query_ap.csv
└── sample_data/
```

## Evaluation

The principal evaluation metric is mean Average Precision (mAP). Per-query AP is also analysed to identify difficult retrieval cases and determine which samples should be used for targeted retraining.

| Experiment | mAP | Improvement |
|---|---:|---:|
| Baseline model | Add verified result | — |
| Dual-model approach | Add verified result | Approximately 3% |

Replace the placeholders above with the exact results produced by the repository.

## Technologies

- Python
- PyTorch
- NumPy
- Pandas
- Jupyter Notebook
- YAML
- Computer Vision
- Image Retrieval

## Dataset

The project uses the VeRI-776 vehicle re-identification benchmark. The dataset is not included in this repository. Users should obtain it from its authorised source and follow the applicable licence and citation requirements.

## Reproduction

1. Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/vehicle-reid-hard-sample-fusion.git
cd vehicle-reid-hard-sample-fusion
```

2. Create and activate a virtual environment.

3. Install the required packages:

```bash
pip install -r requirements.txt
```

4. Download and arrange the VeRI-776 dataset according to the documented folder structure.

5. Update the dataset paths in the YAML configuration files.

6. Run the baseline training and evaluation, followed by hard-sample mining and focused-model training.

Exact commands should be added after the existing notebook has been separated into reproducible training, evaluation and analysis scripts.

## Limitations

- Performance depends on the selected hard-query threshold and focused training subset.
- The current experiments are evaluated on VeRI-776 and may not generalise directly to other datasets.
- Further validation is required before deployment in a production environment.
- Model weights and the VeRI-776 dataset are not stored directly in the repository.

## Acknowledgements

This project builds on publicly available vehicle re-identification research and code. Any external repositories, pretrained models, datasets or implementations used in the project should be explicitly credited here, together with their original licences and citations.

## Author

Vicky Chen  
Master of Data Science  
Sydney, Australia
