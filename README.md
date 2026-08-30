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
├── config.yaml
├── config_dark.yaml
├── dark_image_train.txt
├── model.ipynb
├── ap_lt_0.8.csv
├── vehicle_reid_itsc2023-main 2
│   ├── main.py
│   ├── teste.py
│   ├── ap_bin_counts.csv
├── ap_bin_statistics.png
└── sample_data/
```

## Evaluation

The principal evaluation metric is mean Average Precision (mAP). Per-query AP is also analysed to identify difficult retrieval cases and determine which samples should be used for targeted retraining.

| Experiment | mAP | Improvement |
|---|---:|---:|
| Baseline model | 84.72%  |-|
| Dual-model approach | 87.77% | +3.05 percentage points |

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
git clone https://github.com/VK-bott/vehicle-reid-hard-sample-fusion.git
cd vehicle-reid-hard-sample-fusion
```

2. Create and activate a virtual environment.

3. Download and arrange the VeRI-776 dataset according to the documented folder structure.

4. Update the dataset paths in the YAML configuration files.

5. Run the baseline training and evaluation, followed by hard-sample mining and focused-model training.

Exact commands should be added after the existing notebook has been separated into reproducible training, evaluation and analysis scripts.

## Limitations

- Firstly, the challenging model designed in this fusion mechanism is specifically for vehicle recognition under dim lighting and blurred conditions. However, other complex factors affect the accuracy of vehicle recognition in real-world scenarios. For example, occlusion, viewpoint misalignment, and low resolution etc. The current training data for the challenging model primarily addresses lighting and blur issues, improvements for other factors have not been validated. Therefore, while the applicability and accuracy of Model A have been greatly improved, it still has limitations for complex real-world scenarios and requires further improvement.
- The second limitation is the constraint of computational resources and time. Limited computational resources and training time prevent us from performing large-scale hyperparameter tuning. Parameter tuning is crucial for the model, affecting its learning ability. Currently, our hyperparameters are derived from some of the literature we have read. The results show that our parameters significantly improve model performance. However, due to limitations, we cannot systematically tune our parameters. For example, random search or grid search require substantial computational resources and time, which to some extent limits the true potential of our model.
- Third, overall performance improved during parameter tuning of the challenging model. But limitations in computational resources and time, we lacked ablation experiments for each parameter. In this model, we simultaneously tuned three key parameters such as learning rate, triplet margin, and batch size. Without conducting separate ablation experiments on these three parameters, we could not observe whether individual parameter changes significantly impacted model performance. Furthermore, the lack of parameter sensitivity analysis also made us difficult to observe any interaction effects between parameters. This makes the model somewhat lacking in interpretability.

## Acknowledgements

This project extends the open-source implementation of:

Eurico Almeida, Bruno Silva and Jorge Batista, “Strength in Diversity:
Multi-Branch Representation Learning for Vehicle Re-Identification,”
IEEE ITSC 2023.

Original implementation: [(https://github.com/videturfortuna/vehicle_reid_itsc2023)]

## My Contributions

My contributions include:

- Per-query AP analysis and automated hard-query identification
- Construction of a specialised low-light training subset
- Training and configuration of the focused model
- Dual-model inference and evaluation
- Hyperparameter tuning and experimental comparison
- AP-distribution analysis and visualisation
 the project should be explicitly credited here, together with their original licences and citations.

## Author

Vicky Chen  
Master of Data Science  
Sydney, Australia
