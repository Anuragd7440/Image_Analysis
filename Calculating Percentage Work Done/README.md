# Image Segmentation and Work Progress Analysis

### Task 1: Image Segmentation
The code segments input images by splitting them into two vertical halves. Each half is passed through a pre-trained segmentation model, and the results are then stitched back together to create the final segmented image. The pre-trained model used is available as [test(1).hdf5](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/test(1).hdf5), and two example images used for segmentation are [image_X.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_X.jpg) and [image_Y.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_Y.jpg).

### Task 2: Work Progress Calculation
The segmented images are analyzed to compute the overall work done at a project site. The segmentation results are categorized based on predefined classes, each assigned a specific "work completion" percentage. The program then calculates and compares the work done between two segmented images. You can find the entire implementation in the provided [Colab Notebook](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/Calculating_Perct_Work_Done.ipynb).

## Functions Breakdown

### Segmentation Functions

1. **`segment_and_join(image_path, output_path)`**:
   - Splits an input image vertically into two halves.
   - Segments each half using a pre-trained model ([test(1).hdf5](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/test(1).hdf5)).
   - Stitches the segmented halves back together and saves the result.
   - **Returns**: The final stitched segmented image.

2. **`segment_image(img_path)`**:
   - Prepares an image for segmentation by resizing and normalizing it.
   - Passes the image through the loaded model for segmentation.
   - **Returns**: The segmented image with class predictions.

3. **`save_segmented_image(segmented_image, output_path)`**:
   - Saves a segmented image to the specified path.

4. **`plot_images(original_image, segmented_image)`**:
   - Displays the original grayscale image and the segmented result side by side for visualization.

### Work Progress Calculation Functions

1. **`get_unique_pixel_values_and_areas(image_path)`**:
   - Reads the segmented images and returns a dictionary of unique pixel values and their corresponding counts (areas).

2. **`calculate_distance(pixel, color)`**:
   - Calculates the distance between a pixel value and a class color (in grayscale).

3. **`categorize_pixels(pixel_areas, class_colors)`**:
   - Categorizes pixels into predefined classes based on their grayscale value.
   - Pixels with values ≥5 are classified as "others."

4. **`calculate_overall_work_done(image_path)`**:
   - Calculates the overall work progress for a single image by analyzing the segmented classes and applying predefined work percentages.

5. **`calculate_difference_in_work_done(image1_path, image2_path)`**:
   - Calculates and compares the work done between two images ([image_X.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_X.jpg) and [image_Y.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_Y.jpg)) and returns the difference.

## Class Details and Work Percentages

The code categorizes pixels into the following classes:

| Class Name    | Grayscale Value | Work Completion Percentage |
| ------------- | --------------- | -------------------------- |
| Unlabelled    | 0               | 0%                         |
| Boundary      | 1               | 5%                         |
| Land          | 2               | 10%                        |
| Poles         | 3               | 30%                        |
| Solar Panels  | 4               | 100%                       |
| Others (≥5)   | ≥ 5             | 0%                         |

### Pixel Classification:
- Pixel values less than 5 are classified based on their proximity to these grayscale values.
- Pixels with values ≥5 are considered ambiguous and categorized as "others."

## Output

- **Segmented Images**: The segmented images ([image_X.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_X.jpg) and [image_Y.jpg](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/image_Y.jpg)) are saved as files and can be visualized using the `plot_images` function.
- **Work Progress**: The program prints the overall work progress for both images and the difference in progress between them:
  ```plaintext
  Overall work done on the project site for the first image: 45.67%
  Overall work done on the project site for the second image: 58.23%
  Difference in work done between the two images: 12.56%
  ```

The complete code can be accessed in the [Colab Notebook](https://github.com/Anuragd7440/Image_Analysis/blob/main/Calculating%20Percentage%20Work%20Done/Calculating_Perct_Work_Done.ipynb).
