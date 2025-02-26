readme_content = """
# Skin Lesion Classification & Segmentation Project

This project focuses on the classification of skin lesions using a dataset of images.

## Project Overview

### Dataset
The dataset consists of images of skin lesions, each associated with a target value (either 0 or 1), indicating the presence of one of 7 different types of lesions:

- MEL (Melanoma)
- NV (Melanocytic Nevus)
- BCC (Basal Cell Carcinoma)
- AKIEC (Actinic Keratosis)
- BKL (Benign Keratosis-like Lesions)
- DF (Dermatofibroma)
- VASC (Vascular Lesions)

### Goal
- **Classification** Categorize the 7 types of skin lesions into two targets—malignant or benign—and accurately classify each lesion using a predictive model.

---

## Steps Taken

### 1️⃣ Data Preprocessing

#### Image and Mask Resizing
To ensure that all images and masks are of the same size and compatible for training, we resized both:
- **Images**: Resized to a uniform size of 256x256 pixels, maintaining the aspect ratio by adding padding where necessary.
- **Masks**: Corresponding masks were resized in the same way, ensuring they align with the images.

#### Python Code:
```python
# Resizing images and masks (code example)
from PIL import Image
import os

def resize_and_pad(image, target_size=(256, 256), mode="RGB"):
    # Function implementation for resizing and padding images
    pass
```

---

### 2️⃣ Exploratory Data Analysis (EDA)

We performed **EDA** to understand the distribution of lesion types and ensure the dataset is properly formatted:

#### Steps Taken:
- **Visualized sample images and masks** to ensure correct alignment.
- **Checked pixel distributions** for both images and masks.
- **Examined class distribution** to detect imbalance in the dataset:
  - Found that the dataset is highly imbalanced, with `NV` having the largest number of samples and `DF`, `VASC` underrepresented.

#### Class Distribution:
- MEL = 1113
- NV = 6705
- BCC = 514
- AKIEC = 327
- BKL = 1099
- DF = 115
- VASC = 142

---

### 3️⃣ Balancing the Dataset

Since the dataset is **imbalanced**, we decided to **balance the classes** using a combination of:
- **Undersampling** the dominant class (`NV`).
- **Oversampling** underrepresented classes (`DF` and `VASC`).

The goal was to **balance the dataset** around the size of the `BKL` class (1,099 samples).

#### Updated Dataset:
- **Under-sampled** dominant classes to reduce size to 1,099.
- **Over-sampled** smaller classes to increase them to 1,099 using random duplication.

#### Python Code:
```python
import pandas as pd

# Balance the dataset by undersampling/oversampling
df_balanced = pd.DataFrame()

for lesion in target_columns:
    class_subset = df[df[lesion] == 1]  # Get all samples for this class
    
    if len(class_subset) > target_count:
        # UNDERSAMPLE (reduce class size)
        class_subset = class_subset.sample(target_count, random_state=42)
    else:
        # OVERSAMPLE (duplicate data to increase size)
        class_subset = class_subset.sample(target_count, replace=True, random_state=42)
    
    df_balanced = pd.concat([df_balanced, class_subset])  # Add to final dataset

# Shuffle the dataset and save it as 'balanced_dataset.csv'
df_balanced = df_balanced.sample(frac=1, random_state=42).reset_index(drop=True)
```

---

### Next Steps
1. **Data Splitting**: Split the dataset into training, validation, and test sets (80/10/10 split).
2. **Data Augmentation**: Apply augmentation techniques to prevent overfitting on oversampled classes.
3. **Model Selection**: Choose an appropriate model (ResNet for classification, U-Net for segmentation).
4. **Model Training**: Train the model and evaluate using relevant metrics.

---

## Requirements
- Python 3.x
- Libraries: pandas, numpy, matplotlib, PIL, scikit-learn, tensorflow/keras (for model training)

