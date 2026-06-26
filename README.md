# Document Detection and Perspective Correction

This project detects document boundaries in images with both dark and light backgrounds using classical computer vision techniques. It applies image preprocessing, edge detection, contour analysis, and perspective transformation to extract a top-down view of the document. For better readability, CLAHE is used to enhance contrast on the final warped image.

## Features
- Supports documents on dark and light backgrounds
- Image resizing for faster processing
- Morphological preprocessing to reduce noise
- Canny edge detection and contour-based page extraction
- Hough line processing for challenging light-background cases
- Perspective transform for document rectification
- CLAHE-based contrast enhancement

## Tech Stack
- Python
- OpenCV
- NumPy
- Matplotlib

## How It Works
1. Read and resize the input image if needed
2. Apply morphological operations to clean the image
3. Detect edges with Canny
4. Find the document contour
5. Warp the document using perspective transform
6. Enhance the final result with CLAHE

## Example Use Cases
- Scanning photographed documents
- Extracting paper from messy backgrounds
- Preparing images for OCR or text analysis
