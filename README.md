### Project Overview

This project involves preparing a dataset of skin lesion images and their corresponding masks for model training. The dataset consists of over 10,000 rows, where each row contains an image of a skin lesion and a target value (0 or 1) representing the type of lesion.

### Image Preprocessing

To prepare the images and masks for model training:

1. **Resizing and Padding**:  
   - The original images are of size **600x450** pixels. To standardize the dataset and maintain the aspect ratio, we resize each image and its corresponding mask to the target size (e.g., **256x256** pixels).
   - Since resizing might distort the aspect ratio, padding is added to the images and masks to ensure they fit within the target size without cropping the original content. The padding is applied symmetrically, ensuring the image is centered.

2. **Directories**:
   - The resized images are stored in the folder **`images_resized`**.
   - The resized masks are stored in the folder **`masks_resized`**.

### Script Used for Preprocessing

A Python script utilizing the `Pillow` library (PIL) was used for the following tasks:
- Load images and masks from the **`Images`** and **`Masks`** directories.
- Resize the images and masks while maintaining their aspect ratios.
- Add padding to ensure that the images and masks fit within the target size (256x256 pixels).
- Save the resized and padded images and masks in the respective **`images_resized`** and **`masks_resized`** directories.

This preprocessing ensures the dataset is ready for model training while preserving the original content and structure of the images.
