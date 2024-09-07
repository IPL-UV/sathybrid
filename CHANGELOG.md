# **Changelog**

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## **[Unreleased]**

### **Added**
- Improvements to the image fusion algorithm for better accuracy.
- Added support for new interpolation methods such as `lanczos7`.
- Improved performance of the `find_similar_lr` function.
- Enhanced documentation for new functionalities.

### **Changed**
- Optimized the histogram matching process for speed.
- Updated README with new usage examples.
- Refined error handling in the `image_fusion` function.

### **Fixed**
- Resolved minor bugs related to image normalization.
- Fixed memory leaks in the resampling process.

## **[0.2.0] - 2024-08-27**

### **Added**
- Support for image denoising using SwinIR model.
- Fourier-based fusion with multiple filter options: ideal, Butterworth, Gaussian.
- New utility functions for image kernel application.
- Official support for Python 3.10, 3.11, and 3.12.

### **Changed**
- Improved accuracy of Fourier image fusion for better high-resolution outputs.
- Tweaked color correction algorithms for more precise results in the image fusion process.

### **Fixed**
- Corrected an issue with low-frequency filtering during image fusion.

## **[0.1.1] - 2024-08-26**

### **Added**
- Support for multi-threaded image processing.
- Basic histogram matching between low-resolution and high-resolution images.
  
### **Changed**
- Optimized resampling functions for faster processing.

### **Fixed**
- Resolved bug causing incorrect alignment in high-resolution images.

## **[0.1.0] - 2024-08-10**

### **Added**
- Initial release of `sathybrid` with core functionalities for fusing low-resolution and high-resolution satellite imagery.
- Basic image fusion capabilities using interpolation techniques such as Lanczos and cubic.
- Support for resampling methods and data normalization.

