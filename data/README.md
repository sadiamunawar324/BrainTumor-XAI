# Dataset — Brain Tumor MRI Data

This project uses the **Brain Tumor Dataset** (Kaggle, by Tom Backert), a collection of MRI brain scans for image classification and segmentation. The raw MRI data is **not included in this repository** due to its size — download it from the source below and place it locally before running the notebook.

## 📥 Download

| Source | Link |
|---|---|
| Kaggle | https://www.kaggle.com/datasets/tombackert/brain-tumor-mri-data |

Via the Kaggle CLI:

```bash
pip install kaggle
kaggle datasets download -d tombackert/brain-tumor-mri-data -p ./data
unzip ./data/brain-tumor-mri-data.zip -d ./data/brain_tumor_mri
```

Or with `kagglehub`:

```python
import kagglehub
path = kagglehub.dataset_download("tombackert/brain-tumor-mri-data")
print(path)
```

## 📦 About the dataset

- Collection of MRI brain scans (Kaggle description)
- Tagged for: cancer, biology, image classification, medicine, image segmentation
- **Number of images:** `TODO`
- **Classes:** `TODO` (e.g. `glioma`, `meningioma`, `pituitary`, `notumor`)
- **Train / test split:** `TODO`
- **Image format / resolution:** `TODO`
- **Segmentation masks included:** `TODO (yes/no)`

> ⚠️ The Kaggle page could not be fully read automatically, so the fields marked `TODO` must be filled in from the dataset's *Data Explorer* tab after downloading.

## 🗂 Expected local structure

After downloading and extracting, place the data so the notebook's paths resolve correctly. Adjust the folder names to match what you actually see after extraction:

```
data/
└── brain_tumor_mri/
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

Update `ZIP_PATH` and `EXTRACT_DIR` near the top of your notebook to point at your local copy, e.g.:

```python
ZIP_PATH    = './data/brain-tumor-mri-data.zip'
EXTRACT_DIR = './data/brain_tumor_mri'
```

## 📄 Citation

If you use this dataset, please credit the Kaggle author and any original sources listed on the dataset page:

```bibtex
@misc{backert_brain_tumor_mri_data,
  title        = {Brain Tumor Dataset},
  author       = {Backert, Tom},
  year         = {2024},
  howpublished = {Kaggle},
  url          = {https://www.kaggle.com/datasets/tombackert/brain-tumor-mri-data}
}
```

## ⚖️ License

Refer to the dataset's Kaggle page (linked above) for licensing terms before redistributing or using it commercially.
