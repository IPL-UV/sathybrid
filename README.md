# 

<p align="center">
  <img src="https://huggingface.co/datasets/JulioContrerasH/DataMLSTAC/resolve/main/banner_sathybrid.png" width="100%">
</p>

<p align="center">
    <em>A Python package to fusion LR and HR imagery</em> 🚀
</p>

<p align="center">
<a href='https://pypi.python.org/pypi/satalign'>
    <img src='https://img.shields.io/pypi/v/satalign.svg' alt='PyPI' />
</a>
<a href="https://opensource.org/licenses/MIT" target="_blank">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License">
</a>
<a href="https://github.com/psf/black" target="_blank">
    <img src="https://img.shields.io/badge/code%20style-black-000000.svg" alt="Black">
</a>
<a href="https://pycqa.github.io/isort/" target="_blank">
    <img src="https://img.shields.io/badge/%20imports-isort-%231674b1?style=flat&labelColor=ef8336" alt="isort">
</a>
</p>

---

**GitHub**: [https://github.com/IPL-UV/sathybrid](https://github.com/IPL-UV/sathybrid) 🌐

**PyPI**: [https://pypi.org/project/sathybrid/](https://pypi.org/project/sathybrid/) 🛠️

---

## **Overview** 📊

**Sathybrid** is a Python package designed for fusing low-resolution (LR) and high-resolution (HR) satellite imagery. It allows users to combine spatial and spectral details from different sources, enhancing imagery through methods like Fourier transform fusion and interpolation techniques. The package supports multiple downsampling methods, and it also includes features like image denoising, histogram matching, and kernel-based blurring.

## **Key features** ✨
- **Image fusion**: Combines LR and HR images using Fourier-based interpolation and various resampling techniques (e.g., Lanczos, cubic). 🌍
- **Denoising with SwinIR**: Utilizes the SwinIR model for efficient image denoising prior to fusion. 🧹
- **Custom kernels**: Apply customizable kernels such as Lanczos and cubic for image processing. 🎛️
- **Fourier filtering**: Supports multiple Fourier filters (ideal, Butterworth, Gaussian) for frequency-domain fusion. ⚙️
- **Efficient resampling**: Resizes images with support for different interpolation methods like Lanczos and cubic. 📐

## **Installation** ⚙️
Install the latest version from PyPI:

```bash
pip install sathybrid

```

## **How to use** 🛠️

### **Basic Fusion of HR and LR Imagery** 🛰️

#### **Load libraries**

```python
import sathybrid
import pathlib
```

#### **Define the paths for high-resolution (HR) and low-resolution (LR) images**

```python
PATH = pathlib.Path("/home/cesar/demo/NA5120_E1186N0724/")
HRfile = PATH / "naip" / "m_3812243_nw_10_060_20220524.tif"
LRfile = PATH / "s2" / "s2_image.tif"
OUTfile = PATH / "fusion.tif"
```
#### **Perform the image fusion**
```python
sathybrid.image_fusion(
    hr_file=HRfile,
    lr_file=LRfile,
    output_file=OUTfile,
    scale_factor=8,
    hr_bands=[1, 2, 3],
    hr_normalization=255,
    lr_bands=[3, 2, 1],
    lr_normalization=10_000,
    upsampling_method="lanczos3",
    fourier=True,
    fourier_params={"method": "butterworth", "order": 6, "sharpness": 3},
    denoise=True,
)
```
### **Finding the most similar LR image 🖥️**

#### **Load libraries**

```python
from sathybrid.utils import find_similar_lr
```

#### **Identify the most similar LR image to the HR image based on FFT-L1 similarity**

```python
data_stats = find_similar_lr(
    hr_file=HRfile,
    lr_folder=PATH / "s2",
    hr_bands=[1, 2, 3],
    lr_bands=[3, 2, 1],
    downsampling_method="lanczos3",
    method="fft_l1"
)
```
#### **Get the most similar LR image**

```python
best_lr_image = data_stats.iloc[0]["lr_img"]
print(f"Most similar LR image: {best_lr_image}")
```


### **Applying Custom Kernels**🎛️

#### **Load libraries**

```python
from sathybrid.blur import apply_kernel_to_image
import torch
```

#### **Load a sample image (in PyTorch tensor format)**

```python
image = torch.randn(1, 3, 256, 256).cuda()
```
#### **Apply a triangle kernel**

```python
smoothed_image = apply_kernel_to_image(image, kernel_size=5, method="triangle")
```
## **Advanced Usage** ⚙️

### **Image Denoising with SwinIR** 🧹

#### **Load libraries**

```python
from sathybrid.main import setup_denoiser, image_denoise
```
#### **Initialize the SwinIR denoiser model**

```python
denoiser = setup_denoiser()
```

#### **Load the image to be denoised**

```python
image_tensor = torch.randn(1, 3, 256, 256)
```

#### **Denoise the image**

```python
denoised_image = image_denoise(image_tensor, denoiser)
```


### **Image Fusion with Fourier Transform** 🧮

#### **Load libraries**

```python
from sathybrid.main import image_fusion
```
#### **Define paths for HR, LR, and output**

```python
HRfile = "/path/to/hr_image.tif"
LRfile = "/path/to/lr_image.tif"
OUTfile = "/path/to/output/fusion.tif"
```

#### **Perform fusion with Fourier filtering**

```python
hybrid_image, error = image_fusion(
    hr_file=HRfile,
    lr_file=LRfile,
    output_file=OUTfile,
    scale_factor=4,
    fourier=True,
    fourier_params={"method": "gaussian", "sharpness": 2.5},
    denoise=False,
)
```


## **Supported features and filters** ✨

- **Resampling methods:**
    - `lanczos3`, `lanczos5`, `lanczos7`, `cubic`, `nearest`.

- **Fourier filters:**
    - `ideal`, `butterworth`, `gaussian`, `sigmoid`