# Skin Lesion Classification Project

This project focuses on the classification of skin lesions using a dataset of images.

## Project Overview

### Dataset
The dataset consists of images of skin lesions, each associated with a target value (either 0 or 1), indicating the presence of one of 7 different types of lesions:

- **MEL (Melanoma)**
- **NV (Melanocytic Nevus)**
- **BCC (Basal Cell Carcinoma)**
- **AKIEC (Actinic Keratosis)**
- **BKL (Benign Keratosis-like Lesions)**
- **DF (Dermatofibroma)**
- **VASC (Vascular Lesions)**

### Goal
- **Classification**: Categorize the 7 types of skin lesions into two targets—**suspicious** and **non-suspicious**—and accurately classify each lesion using a predictive model.

### Target Definition
- **Suspicious**:  
  - **MEL (Melanoma)** – Malignant skin cancer  
  - **AKIEC (Actinic Keratosis)** – Precancerous lesion  
- **Non-Suspicious**:  
  - **NV (Melanocytic Nevus)**  
  - **BCC (Basal Cell Carcinoma)**  
  - **BKL (Benign Keratosis-like Lesions)**  
  - **DF (Dermatofibroma)**  
  - **VASC (Vascular Lesions)**  

## Model Approach
The project utilizes deep learning models to classify skin lesions based on their images. A convolutional neural network (CNN) is trained on the dataset, leveraging transfer learning with **EfficientNetB3** for improved accuracy.

---

## Steps Taken

### 1️⃣ Data Preprocessing

#### Image and Mask Resizing
To ensure that all images and masks are of the same size and compatible for training, we resized both:
- **Images**: Resized to a uniform size of 256x256 pixels, maintaining the aspect ratio by adding padding where necessary.
