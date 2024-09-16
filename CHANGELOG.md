# **Changelog**

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## **[Unreleased]**

### **Added**
- Implemented advanced fusion techniques for combining low-resolution (LR) and high-resolution (HR) satellite imagery.
- Added support for multi-scale fusion to preserve both spatial and spectral details.
- New logging functionality for tracking image processing steps.

### **Changed**
- Improved performance for large-scale fusion processes.
- Updated user documentation with additional examples for LR-HR image fusion.

### **Fixed**
- Resolved bug related to memory overflow during fusion of large imagery sets.
- Fixed minor inaccuracies in the fusion process.

## **[0.2.0] - 2024-08-27**

### **Added**
- New functionality for fusion of LR and HR satellite images.
- Support for Python 3.12.
- New user guide with detailed examples for fusion methods.

### **Changed**
- Improved algorithm for faster fusion and reduced computational load.

## **[0.1.1] - 2024-08-26**

### **Added**
- Added new methods to improve the handling of noisy satellite imagery during the fusion process.

### **Fixed**
- Bug fix: Addressed an issue where certain imagery would cause memory leaks during processing.

## **[0.1.0] - 2024-08-10**

### **Added**
- Initial release of `sathybrid` for fusing low-resolution and high-resolution satellite imagery.
- Basic fusion functionalities and initial documentation.