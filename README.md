# **ENPM673 - Camera Calibration & Stereo Vision System (Project 3)**

## **Project Overview**
This project is part of **ENPM673 - Perception for Autonomous Robots** at the **University of Maryland, College Park**.  
The objective is to implement a **Single Camera Calibration Pipeline** and a **Stereo Vision System** for **depth estimation and 3D reconstruction**.

The project consists of **two main tasks**:

1. **Single Camera Calibration**
   - Perform **intrinsic and extrinsic calibration** using a chessboard or circular pattern.
   - Detect **corners or centroids** and optimize calibration parameters.
   - Compute **reprojection errors** to analyze accuracy.
   - Visualize **undistorted images** and reprojected points.

2. **Stereo Vision System**
   - Identify **feature correspondences** between stereo images.
   - Compute the **Fundamental & Essential matrices**.
   - Perform **image rectification & disparity estimation**.
   - Generate a **depth map** from stereo images.

---

## **Table of Contents**
- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
  - [Step 1: Clone the Repository](#step-1-clone-the-repository)
  - [Step 2: Install Dependencies](#step-2-install-dependencies)
  - [Step 3: Running the Jupyter Notebook](#step-3-running-the-jupyter-notebook)
- [Running the Project](#running-the-project)
- [About the Project](#About-the-project)
  - [Problem 1: Single Camera Calibration](#problem-1-single-camera-calibration)
  - [Problem 2: Stereo Vision System](#problem-2-stereo-vision-system)
- [Project Structure](#project-structure)
- [How the Code Works](#how-the-code-works)
- [Authors](#authors)
- [License](#license)

---

## **Features**
✔ **Single Camera Calibration** using **Chessboard or Circular Grid Patterns**.  
✔ **Feature Detection** using **Harris Corner Detector** or **Blob Detection**.  
✔ **Reprojection Error Analysis** using **Mean Squared Error (MSE)**.  
✔ **Stereo Rectification** to align epipolar lines in stereo images.  
✔ **Disparity Map Computation** for **depth estimation**.  
✔ **Visualization of Calibration Results** including **corner detection & image rectification**.  

---

## **Installation**
### **Prerequisites**
Ensure you have the following dependencies installed:
- **Python 3.8+**
- **Jupyter Notebook**
- **OpenCV**
- **NumPy**
- **Matplotlib**
- **SciPy**
- **Scikit-Image**
- **Scikit-Learn**

### **Step 1: Clone the Repository**
```bash
git clone <your-repository-url> enpm673_project3
cd enpm673_project3
```
### **Step2: Install Dependencies**
Install the required Python packages:

```bash
pip install numpy opencv-python matplotlib scipy scikit-image scikit-learn


```

### **Step 3: Running the Jupyter Notebook**
```
jupyter notebook

```
Then, open harshav_project3.ipynb in Jupyter and execute the code step by step.
## **Running the Project**
Since your work is in Jupyter Notebook format, follow these steps:
- Open the Jupyter Notebook:
```
 jupyter notebook 
 ```
- Navigate to harshav_project3.ipynb.
- Run each cell step by step.

## **About the Project**
### **Problem 1: Single Camera Calibration**
Command to Run

**Processing Pipeline**
- Reads video frames using OpenCV.
- Removes blurry frames using Variance of Laplacian (Threshold = 150).
- Converts images to grayscale.
- Detects edges using Canny Edge Detection.
- Extracts Hough Lines from detected edges.
- Identifies intersecting lines as potential corners.
- Verifies corners using Harris Corner Detector.
- Overlays the boundary (blue lines) and corners (red dots) on the output video.
**Expected Output**
- A video file with corner-detected frames.
- Removed blurry frames count displayed in the console.

### **Problem 2: Image Stitching for Panorama**

**Processing Pipeline**
Loads 4 input images.
- Extracts features using SIFT, ORB, or another feature extractor.
- Matches features using FLANN or brute-force matcher.
- Uses RANSAC to filter out bad matches.
- Computes homographies between image pairs.
- Warps images onto a common plane.
- Blends images to create a final stitched panorama.
**Expected Output**
- A stitched panoramic image saved as panorama.jpg.

## **Project Structure**
```
enpm673_project3/
├── harshav_project3.ipynb      # Jupyter Notebook for execution
├── input/
│   ├── calibration_images/      # Input images for camera calibration
│   ├── stereo_images/           # Stereo image pairs for depth estimation
│
├── output/
│   ├── undistorted_images/      # Output undistorted images
│   ├── depth_map/               # Output depth maps (heatmap & grayscale)
│
├── README.md                    # Documentation


```

## **How the Code Works**
**1. Paper Corner Detection**
- Reads each video frame.
- Removes blurry frames using Variance of Laplacian.
- Detects edges using Canny.
- Finds lines using Hough Transform.
- Extracts intersections (putative corners).
- Validates corners using Harris Corner Detector.
- Overlays the edges and corners onto the video.
**2. Image Stitching**
- Extracts keypoints using SIFT/ORB.
- Matches keypoints between consecutive images.
- Filters incorrect matches using RANSAC.
- Computes homographies to warp images together.
- Blends images to create a seamless panoramic output.
