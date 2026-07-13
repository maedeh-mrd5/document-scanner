# 📄 Document Detection from Images and Videos



This project implements a robust **document detection algorithm** for both **images** and **videos** using OpenCV. The algorithm is designed to work under different background and lighting conditions by adapting its detection strategy according to the visual characteristics of the document.



## Features



* Document detection in both images and videos

* Adaptive algorithm based on document/background similarity

* Robust contour detection

* Morphological gap filling for incomplete document edges

* Automatic best frame selection from videos

* Perspective correction using the detected document corners



---



## Algorithm



The proposed algorithm uses two different strategies depending on the similarity between the document color and the surrounding background.



### Case 1: Document and Background Have Similar Colors



When the document color is close to the background color, edge-based methods become unreliable. Therefore, two complementary approaches are used:



### Method 1: Content-Based Detection



The document is localized according to its internal textual and structural content rather than relying only on color differences.



### Method 2: Bounding Region Estimation



If content detection is insufficient:



* Very small contours are removed as noise.

* The leftmost and topmost points are found.

* The rightmost and bottommost points are found.

* These extreme points are used to estimate the document boundary.



---



### Case 2: Document and Background Have Different Colors



When sufficient contrast exists between the document and the background, the following pipeline is applied:



1. Remove document text to simplify the page structure.

2. Apply Canny edge detection.

3. Detect the document contour and extract its four corners.

4. If a complete contour cannot be detected (usually because of broken page edges), perform large-scale morphological closing to fill the gaps.

5. Detect the document contour again.

6. Apply perspective transformation to obtain the final scanned document.



---



## Video Processing



For videos, the above detection algorithm is applied independently to every frame.



A custom **frame scoring function** evaluates each detected document based on detection quality (such as contour completeness and geometric consistency).



The frame with the highest score is selected as the final output.



---



## Project Structure



```

├── image_scanner.ipynb      # Document detection for images

├── video_scanner.ipynb      # Document detection for videos

├── images/

├── videos/

└── README.md

```



---



## Technologies



* Python

* OpenCV

* NumPy

* Matplotlib



---



## Processing Pipeline



```

Input Image / Video

        │

        ▼

Check Background Similarity

        │

 ┌──────┴─────────┐

 │                │

 ▼                ▼

Similar Colors    Different Colors

 │                │

Content-Based     Remove Text

Detection         ↓

 │             Canny Edge Detection

Bounding Box       ↓

Estimation      Contour Detection

 │                │

 └──────┬─────────┘

        ▼

Morphological Closing (if needed)

        ▼

Corner Detection

        ▼

Perspective Transformation

        ▼

Final Scanned Document
