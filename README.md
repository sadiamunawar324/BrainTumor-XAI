# Brain Tumor MRI Classification with Explainable AI (XAI)

This project trains and compares three deep learning approaches for classifying brain tumors from MRI scans, then rigorously evaluates **which explainability method (Grad-CAM, Integrated Gradients, LIME, SHAP) best explains each model's predictions** — with a particular focus on the hardest tumor class, meningioma.

## Overview

The notebook (`BT_XAI.ipynb`) covers a full pipeline:

1. **Data preparation** — extracts a brain tumor MRI dataset, splits it 70/30 into train/test, and generates a brain-masked version of the dataset so both training and XAI visualizations ignore background/skull-exterior pixels.
2. **Model training** — builds and fine-tunes three classifiers:
   - **ResNet50** (transfer learning, last 100 layers fine-tuned)
   - **DenseNet121** (transfer learning, last 100 layers fine-tuned)
   - **CNN–XGBoost Hybrid** (custom residual CNN feature extractor + XGBoost classifier)
3. **Statistical model comparison** — McNemar's test (overall and per-class) to determine whether performance differences between models are statistically significant, plus standard metrics (accuracy, precision, recall, F1, Cohen's kappa, ROC-AUC, confusion matrices).
4. **Explainable AI (XAI) analysis** — applies and compares four interpretability techniques across models:
   - **Grad-CAM**
   - **Integrated Gradients**
   - **LIME**
   - **SHAP**
5. **XAI evaluation framework** — scores each explanation method using:
   - AOPC Deletion (region removal impact)
   - AOPC Insertion (region addition impact)
   - Faithfulness (Spearman correlation)
   - A weighted **composite interpretability score**: `0.25 × (1 − AOPC Deletion) + 0.25 × AOPC Insertion + 0.50 × Faithfulness`

## Dataset

The notebook expects a zipped brain tumor MRI dataset (`BrainTumour.zip`) containing class-labeled subfolders of images (e.g. glioma, meningioma, pituitary, no tumor). Update `ZIP_PATH` in the notebook to point to your dataset archive.

## Requirements

```
tensorflow
scikit-learn
scikit-image
opencv-python
xgboost
statsmodels
shap
lime
numpy
pandas
matplotlib
seaborn
scipy
```

Install with:

```bash
pip install tensorflow scikit-learn scikit-image opencv-python xgboost statsmodels shap lime numpy pandas matplotlib seaborn scipy
```

A GPU is strongly recommended for training the CNN models and running SHAP/Integrated Gradients, which are computationally expensive.

## Usage

1. Place `BrainTumour.zip` in the working directory (or update `ZIP_PATH`).
2. Open and run `BT_XAI.ipynb` top to bottom in Jupyter or Google Colab.
3. Notebook sections can largely be run independently once models are trained and predictions/artifacts (`.npy`, `.h5`) are saved, since later cells reload saved predictions and models rather than recomputing everything.

## Repository Structure

```
.
├── BT_XAI.ipynb        # Main notebook: training, evaluation, and XAI comparison
└── README.md
```

## Key Results Produced

- Trained model checkpoints (e.g. `best_resnet50_model.h5`)
- Saved prediction arrays for statistical testing (`y_true.npy`, `y_pred_densenet.npy`, `y_pred_cnn_xgb.npy`)
- Per-model and per-class performance comparison tables/plots
- Side-by-side Grad-CAM / Integrated Gradients / LIME / SHAP visualizations, including meningioma-specific analysis
- A final ranked comparison table scoring each XAI method by faithfulness and reliability

## Notes

- Random seeds are fixed (`42`) for reproducibility.
- A custom brain-masking step (using OpenCV + scikit-image morphology) is applied before training and before generating heatmaps, to prevent models and explanations from attending to non-brain background regions.
- Mixed precision training is enabled where available to speed up SHAP/Integrated Gradients computation.
