# Dataset — Brain Tumor MRI Data

This project uses the *Brain Tumor MRI Data* dataset. The raw MRI data is *not included in this repository* due to its size — download it from the source below and place it locally before running the notebook.

# Download

| Source | Link |
|---|---|
| Kaggle (this upload) | https://www.kaggle.com/datasets/tombackert/brain-tumor-mri-data |
| Kaggle (combined source dataset) | https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset |
| figshare (glioma / meningioma / pituitary source) | https://doi.org/10.6084/m9.figshare.1512427 |
| Kaggle (SARTAJ source, glioma/meningioma/pituitary/notumor) | https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri |
| Kaggle (Br35H source, notumor images) | https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection |

> Note: this upload appears to build on the widely-used [Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset), which itself combines the figshare, SARTAJ, and Br35H sources above (glioma / meningioma / notumor / pituitary, ~7,023 images total). If `tombackert`'s upload differs in size, split, or class names, update the details below to match what you see on the Kaggle "Data" tab.

# About the dataset

- **~7,023 MRI scans** *(verify against the Kaggle file count)*
- **4 classes**: `glioma`, `meningioma`, `pituitary`, `notumor`
- Pre-split into **Training / Testing** folders *(verify against the Kaggle "Data" tab)*
- Images vary in size — resize/crop during preprocessing
- Underlying source data combines the figshare, SARTAJ, and Br35H brain tumor datasets

# Expected local structure

After downloading and extracting, place the data so the notebook's paths resolve correctly:

```
data/
└── brain-tumor-mri-data/
    ├── Training/
    │   ├── glioma/
    │   ├── meningioma/
    │   ├── pituitary/
    │   └── notumor/
    └── Testing/
        ├── glioma/
        ├── meningioma/
        ├── pituitary/
        └── notumor/
```

Update `ZIP_PATH` and `EXTRACT_DIR` near the top of the notebook to point at your local copy, e.g.:

```python
ZIP_PATH    = './data/brain-tumor-mri-data.zip'
EXTRACT_DIR = './data/brain-tumor-mri-data_extracted'
```

# Citation

Please refer to the dataset's Kaggle page for the author's preferred citation, and cite the original combined sources where applicable:

- Cheng, J. (2017). *Brain tumor dataset* (figshare). https://doi.org/10.6084/m9.figshare.1512427
- Bhuvaji, S. et al. *Brain Tumor Classification (MRI)* (SARTAJ, Kaggle). https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri
- Hamada, A. (2020). *Br35H :: Brain Tumor Detection 2020* (Kaggle). https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection

# License

Refer to the dataset's Kaggle page (linked above) for licensing terms before redistributing or using it commercially.
