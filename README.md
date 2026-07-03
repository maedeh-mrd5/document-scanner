# Automatic Document Detection and Perspective Correction

This project implements an automatic document detection and scanning pipeline using **Python** and **OpenCV**. The algorithm detects a document from an input image, corrects its perspective, removes shadows, and produces a clean, scanner-like output.

## Features

- Automatic document detection
- Adaptive processing pipeline based on image contrast
- Perspective transformation
- Shadow removal
- Noise reduction
- Contrast enhancement using CLAHE
- Edge detection using Canny and Sobel operators
- Morphological operations for robust page extraction
- Visualization of every processing stage

## Processing Pipeline

The algorithm first analyzes the image to determine whether the foreground and background have sufficient contrast.

### High-Contrast Images

For images with good contrast, the following steps are applied:

1. Canny edge detection
2. Contour extraction
3. Convex hull approximation
4. Quadrilateral detection
5. Perspective transformation
6. Shadow removal
7. Adaptive thresholding

### Low-Contrast Images

For challenging images with low contrast, the pipeline uses additional enhancement steps:

1. Convert image to LAB color space
2. Extract luminance channel
3. Gaussian blur
4. CLAHE contrast enhancement
5. Bilateral filtering
6. Sobel edge detection
7. Otsu thresholding
8. Morphological closing
9. Contour detection
10. Perspective correction
11. Shadow removal

## Project Structure

```
project/
│
├── images/
│   ├── input_1.jpg
│   ├── input_2.jpg
│   └── ...
│
├── document_detection.py
└── README.md
```

## Requirements

Install the required libraries:

```bash
pip install numpy matplotlib opencv-python
```

## Usage

Place your input images inside the `images/` directory.

Run the script:

```bash
python document_detection.py
```

The program processes each image and displays:

- Original Image
- Edge Detection
- Detected Document
- Perspective Corrected Image
- Final Scanned Result

## Main Techniques Used

- OpenCV
- NumPy
- Gaussian Blur
- Bilateral Filtering
- CLAHE
- Sobel Operator
- Canny Edge Detection
- Otsu Thresholding
- Morphological Operations
- Convex Hull Detection
- Perspective Transform
- Adaptive Thresholding

## Output

The algorithm produces a scanner-like image by:

- Detecting the document boundary
- Correcting perspective distortion
- Removing uneven illumination and shadows
- Enhancing text readability

## Example Workflow

```
Input Image
      ↓
Contrast Analysis
      ↓
Adaptive Detection Pipeline
      ↓
Page Detection
      ↓
Perspective Correction
      ↓
Shadow Removal
      ↓
Final Scanned Document
```

## Applications

- Mobile document scanning
- OCR preprocessing
- Receipt digitization
- Book page extraction
- Automatic document cropping
- Digital archiving

## Author

Developed as a Computer Vision project using Python and OpenCV.
