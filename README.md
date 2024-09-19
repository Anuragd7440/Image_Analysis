# Project Overview

This repository contains three essential workflows for image segmentation and work progress analysis:

1. **[Label Studio to Grayscale Mask Conversion Pipeline](https://github.com/Anuragd7440/Image_Analysis/tree/main/Creating%20Masks)**: Converts annotated images from Label Studio into grayscale masks.
2. **[Image Segmentation with U-Net](https://github.com/Anuragd7440/Image_Analysis/tree/main/Segmentation%20Code)**: A step-by-step guide for training and generating a U-Net model.
3. **[Work Progress Analysis](https://github.com/Anuragd7440/Image_Analysis/tree/main/Calculating%20Percentage%20Work%20Done)**: A tool for image segmentation and calculating work completion.

## Folder 1: [Label Studio to Grayscale Mask Conversion Pipeline](https://github.com/Anuragd7440/Image_Analysis/tree/main/Creating%20Masks)

This notebook converts Label Studio annotations into grayscale masks, renames the images, and zips them for download.

### Steps to Execute:
1. Open `COCO_JSON_to_Semantic_Masks.ipynb` in Google Colab.
2. Upload your Label Studio export (JSON format) and raw drone-captured images.
3. Follow the steps within the notebook to convert the annotations into grayscale masks.
4. The grayscale masks and renamed images will be saved and zipped for download.

## Folder 2: [Image Segmentation with U-Net](https://github.com/Anuragd7440/Image_Analysis/tree/main/Segmentation%20Code)

This notebook provides steps to train a U-Net model for image segmentation. Instead of outputting segmented images, a trained model will be generated, which you can download and use later.

### Steps to Execute:
1. Open `MultiClass_Segmentation.ipynb` in Google Colab.
2. Upload or link the preprocessed images.
3. Run the cells to train the U-Net model on your dataset.
4. Once training is complete, the model will be saved and downloadable for future use.

## Folder 3: [Work Progress Analysis](https://github.com/Anuragd7440/Image_Analysis/tree/main/Calculating%20Percentage%20Work%20Done)

This folder includes two tasks: segmenting images and analyzing the work progress.

### Task 1: Image Segmentation
- You will need to manually analyze the dimensions of the input images. If the image is large, manually modify the code to split the image into smaller subimages. Each subimage is then segmented individually using the trained U-Net model. After segmentation, the subimages should be joined back together in their original positions to reconstruct the full segmented image.

### Task 2: Work Progress Calculation
- Calculates work completion percentages based on predefined class mappings from the segmentation results.

### Steps to Execute:
1. Open `Calculating_Perct_Work_Done.ipynb` in Google Colab.
2. Manually analyze the input image dimensions and adjust the code as needed to split the images into subimages.
3. Run the cells to perform segmentation on the subimages and join them based on their original positions.
4. Continue to calculate the work progress percentages based on class mappings.
5. The results will be displayed in the notebook.
