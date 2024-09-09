# Label Studio to Grayscale Mask Conversion Pipeline

## Overview

This pipeline guides through the process of annotating drone-captured images using Label Studio, exporting the annotations, and generating grayscale masks based on a predefined label mapping. The raw images and the corresponding grayscale masks are saved separately and renamed sequentially, then zipped for download.

## Workflow

### 1. Image Annotation with Label Studio

- **Step 1**: Import the raw images captured by drones into Label Studio.
  - Ensure the images are of the desired format and resolution for annotation.
  
- **Step 2**: Annotate the images using the **Polygon Tool** (preferred) or **Paint Brush**.
  - **Polygon Tool**: Ideal for precise segmentation (e.g., solar panels).
  - **Paint Brush**: Useful for more freeform or irregular shapes.
  
- **Step 3**: Annotate all relevant regions, ensuring correct and consistent labeling across images.
  
- **Step 4**: Save the annotations after completion.

### 2. Exporting Annotations in COCO Format

- **Step 5**: Export the dataset from Label Studio in **COCO JSON format**.
  - The exported zip file will include:
    - A `JSON` file containing annotations.
    - A directory containing the raw annotated images.

### 3. Uploading and Processing the Exported Data in Colab

- **Step 6**: Upload the exported zip file to your Colab environment.
  - The zip file contains the `JSON` file and the images directory.

- **Step 7**: Unzip the file in Colab. The notebook will:
  - Read the images and `JSON` annotation file.
  - Map the categories (e.g., `Boundary`, `Land`, `Solar_Panels`, etc.) to grayscale values based on predefined mappings.

### 4. Generating and Saving Grayscale Masks

- **Step 8**: For each image:
  - A **semantic grayscale mask** is created based on polygon annotations.
  - The mask values correspond to specific classes using a mapping:
    - `Unlabelled`: 0 (Black)
    - `Boundary`: 1 (Light Blue)
    - `Land`: 2 (Light Green)
    - `Others`: 3 (Orange)
    - `Solar_Panels`: 4 (Brown)

- **Step 9**: The notebook converts each polygon segmentation into a **filled grayscale mask** using OpenCV's `fillPoly` function.

- **Step 10**: Both the raw images and masks are renamed sequentially:
  - Images are renamed to `image_no{x}.JPG`.
  - Corresponding grayscale masks are renamed to `image_no{x}.png`.

- **Step 11**: The raw images are moved to the images directory, and the masks are saved in the **semantic_masks** directory.

### 5. Downloading the Processed Data

- **Step 12**: After generating the semantic masks and renaming the images, the notebook will create a downloadable zip file containing:
  - The renamed **raw images**.
  - The corresponding **grayscale masks**.

## Notes

- **Error Handling**: If a file is missing, it skips that image and logs a message.
- **Polygon Annotations**: For unrecognized category ID, the code defaults to the `Unlabelled` class with a grayscale value of `0`.
- **Output Structure**: The raw images and their masks are saved with corresponding sequential names, ensuring easy matching between images and masks for training or further processing.
