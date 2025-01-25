# Candlestick Data Extraction and Enhancement

This project is designed to process candlestick images (financial charts) and extract the maximum and minimum points of the candlesticks, representing these points on a Cartesian plane. Additionally, the code enhances the visualization of the candles using image processing techniques such as edge detection and color enhancement.

## Technologies Used

- **OpenCV**: For image processing.
- **NumPy**: For efficient array manipulation.
- **Pandas**: For creating and handling tabular data.
- **Matplotlib**: For visualizing graphs.

## Main Functions

### 1. `fill_gaps(image, start_point, channel, mask, value, direction, max_gap_length=20, max_search_range=5)`

This function fills in gaps in the image, extending the color channel value in a given direction to complete empty areas within the specified limits.

- **Parameters**:
  - `image`: The image on which the operation will be applied.
  - `start_point`: The starting point for filling the gap.
  - `channel`: The color channel to modify (0 for blue, 1 for green, 2 for red).
  - `mask`: A mask of the image that determines the areas to fill.
  - `value`: The value used to fill the gap.
  - `direction`: Direction in which to fill the gap (1 or -1).
  - `max_gap_length`: Maximum length of the gap that can be filled.
  - `max_search_range`: The maximum search range to fill the gap.

### 2. `enhance_color(image, color_mask, brightness_factor=1.5)`

This function enhances the color of the candles in the image by increasing the brightness and applying a color mask.

- **Parameters**:
  - `image`: The original image to enhance.
  - `color_mask`: The mask defining the areas to enhance.
  - `brightness_factor`: The factor to increase the brightness of the image.

### 3. `filter_small_columns(image, threshold=2)`

Removes small columns in the image that don't contain enough visual information.

- **Parameters**:
  - `image`: The image to filter.
  - `threshold`: The threshold below which columns will be removed.

### 4. `extract_candlestick_data(image_path, output_excel_path)`

This is the main function that processes a candlestick image, detects green and red candles, enhances the images, and extracts the maximum and minimum points of the candles on the Cartesian plane. It then saves the results in an Excel file.

- **Parameters**:
  - `image_path`: Path to the candlestick image to process.
  - `output_excel_path`: Path to save the resulting Excel file.

## Preprocessing Image (Upscaling)

Before running the data extraction, **it is recommended to first upscale the image**. This is important because upscaling enhances the image's resolution, which allows for better detection of candlestick features such as the candle body and wicks. You can use any upscaling technique or tool (such as ESRGAN or Real-ESRGAN) to upscale the image to a higher resolution.

Once the image has been upscaled, you can proceed with running the `extract_candlestick_data()` function to extract and enhance the candlestick data.

## Requirements

Make sure you have the following libraries installed to run the code:

```bash
pip install opencv-python-headless numpy pandas matplotlib
