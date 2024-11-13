# 📝 Label-Free, Two-Photon Image Resolution Enhancement Using a Deep-Learning Autoencoder Algorithm

---

### 👥 Authors (of the overall research project):
- **Tien Long Dinh**¹*, **Christopher M. Polleys**¹, **Nilay Vora**¹, **Hong-Thao Thieu**², **Elizabeth Genega**³, and **Irene Georgakoudi**¹⁴  
  - ¹ Department of Biomedical Engineering, Tufts University, Medford, MA, USA  
  - ² Department of Obstetrics and Gynecology, Tufts Medical Center, Boston, MA, USA  
  - ³ Department of Pathology and Laboratory Medicine, Tufts Medical Center, Boston, MA, USA  
  - ⁴ Cell, Developmental, and Molecular Biology Program, Tufts University, Boston, MA, USA  

---

## 🧠 Model Training

These notebooks implement model training experiments to enhance resolution in low-resolution microscopy images for downstream analysis of mitochondrial clustering and redox ratio extraction. Models—RCAN, CARE, CycleGAN, and SRGAN are experimented to restore fine structural and metabolic details in cervical tissue images. Each notebook supports full-image and patch-based training, with outputs in .npz format. These notebooks were used for quick development and testing of models prior to conversion into training pipeline scripts deployed on high-performance computers at Tufts University. Full scripts and the complete pipeline are not included here.

```plaintext
├── model_training/
│   ├── RCAN_standard.ipynb         # Trains RCAN for super-resolution on 2D images, with optional patching and SSIM evaluation
│   ├── CSBDeep_experiment.ipynb    # Trains CSBDeep for denoising microscopy images, with optional patch-based processing
│   ├── CARE_patch_train.ipynb      # Trains CARE for 2D image denoising, supporting full and patch-based input
│   ├── CARE_patch_train_3D.ipynb   # Trains CARE for 3D image stack denoising with depth-based patching
│   ├── CycleGAN_UTOM.ipynb         # Trains CycleGAN for unsupervised content-preserving transformation
│   └── SRGAN.ipynb                 # Trains SRGAN for photorealistic single-image super-resolution
```

---

### 🖼️ `RCAN_standard.ipynb`

Implements the **Residual Channel Attention Network (RCAN)**, a deep convolutional neural network (CNN) model for 2D image super-resolution. RCAN upscales low-resolution images while preserving fine details, using residual connections to stabilize training and channel attention mechanisms to emphasize important features. Based on *[Image Super-Resolution Using Very Deep Residual Channel Attention Networks, ECCV 2018](https://openaccess.thecvf.com/content_ECCV_2018/papers/Yulun_Zhang_Image_Super-Resolution_Using_ECCV_2018_paper.pdf)* by Yulun Zhang et al.

### 🧪 `CSBDeep_experiment.ipynb`, 🔍 `CARE_patch_train.ipynb`, and 🧬 `CARE_patch_train_3D.ipynb`

All three notebooks use **Content-Aware Image Restoration (CARE)**, a supervised deep convolutional autoencoder designed for denoising and restoring microscopy images. CARE learns to remove noise and enhance image quality from paired low- and high-quality images. 

- **CSBDeep_experiment.ipynb**: Implements CARE for denoising noisy microscopy images, supporting both full and patch-based data with optional normalization. Based on *[CARE: Content-Aware Image Restoration, Nature Methods 2018](https://doi.org/10.1038/s41592-018-0216-7)* by Martin Weigert et al.
- **CARE_patch_train.ipynb**: Adapts CARE to process 2D microscopy images with both full-image and overlapping patch options, saving results in `.npz` format for 2D denoising applications.
- **CARE_patch_train_3D.ipynb**: Extends CARE to handle 3D microscopy stacks, utilizing depth-based patching to reduce noise in volumetric image data.

### 🔄 `CycleGAN_UTOM.ipynb`

Implements **Cycle-Consistent Generative Adversarial Network (CycleGAN)**, a semi-supervised model for transforming images between domains using two unpaired datasets. CycleGAN enables content-preserving transformations between imaging modalities where paired datasets are unavailable, maintaining essential structural details while transforming the "style". Based on *[Unsupervised Content-Preserving Transformation for Optical Microscopy, Light Sci Appl 2021](https://www.nature.com/articles/s41377-021-00484-y)* by Li et al.

### 🌄 `SRGAN.ipynb`

Applies **Super-Resolution Generative Adversarial Network (SRGAN)**, a model that enhances low-resolution images to high-resolution outputs with photorealistic details. SRGAN’s adversarial training produces high-quality textures, making it suitable for applications requiring realistic image enhancement. Based on *[Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network, arXiv 2017](https://arxiv.org/abs/1609.04802)* by Christian Ledig et al.

---

## 📊 Data Processing

These notebooks supported the development of data processing strategies for model training pipelines, applying and evaluating normalization, illumination correction, and patching implementations. Processed data is exported as train-test-validation `.npz` files.

```plaintext
├── data_processing/
│   ├── mat_to_npz_processing.ipynb       # Converts .mat files to .npz with normalization and patching
│   ├── patch_preprocessing_3D.ipynb      # Prepares 3D image stacks with depth-based patching
│   └── patch_preprocessor.ipynb          # Processes 2D images with patching and normalization 
```

### 📝 `mat_to_npz_processing.ipynb`

Converts `.mat` image stacks into `.npz` format with flexible normalization options, such as percentile clipping, and customizable patching methods. Implements and evaluates impact of illumination correction.

### 🔧 `patch_preprocessor.ipynb`

Prepares 2D images with overlapping patches and multiple normalization options. Outputs are uniform patches in `.npz` format.

### 🧩 `patch_preprocessing_3D.ipynb`

Processes 3D image stacks, creating depth-based patches suitable for 3D models. Performs depth normalization and evaluates impact of different strategies.

---
![image](https://github.com/user-attachments/assets/cb2a1984-322d-4b45-9fe8-466163118310)

---

### 📄 250-Word Abstract:
Non-invasive, label-free microscopy systems have seen significant improvements in imaging quality for tissue analysis and diagnostics. High lateral imaging resolution in novel ex vivo imaging systems has enabled the development of algorithms to extract functional information from living tissues. However, in vivo clinical microscopic imaging systems may have limited imaging resolution to extract relevant functional information. Modifying clinical imaging hardware to increase resolution can be constrained by regulatory and engineering challenges. Therefore, low-resolution (LR) images require computational methods to recover important signals. 

Deep autoencoding neural networks have demonstrated substantial signal restoration and resolution enhancement in microscopic imaging. This study aims to restore functional metrics from LR images of human cervical tissue using supervised and unsupervised deep autoencoding algorithms. A total of 724 images of reduced nicotinamide adenine dinucleotide (phosphate) (NAD(P)H) and flavoproteins were acquired ex vivo using two-photon excited fluorescence within freshly excised stratified squamous epithelial tissues. A supervised deep convolutional autoencoder and a reversible unsupervised deep learning algorithm were trained using overlapping patches of LR images as inputs and paired high-resolution (HR) image patches as ground truths.

Optical redox ratio and mitochondrial clustering in restored images are evaluated to assess the impact of algorithms on functional metrics extraction. The reversed unsupervised algorithm reduces the resolution of HR images to quantitatively assess the impact of LR imaging on metabolic information acquisition. Improved functional metrics extraction in the clinical environment is expected to accelerate the clinical translation of novel non-invasive diagnostic solutions.

---

### 🔍 100-Word Summary:
Microscopic imaging systems with high resolution (HR) enable extraction of functional information for disease diagnosis within living tissues. However, in vivo clinical microscopic imaging systems may have limited imaging resolution to extract relevant functional information. This study aims to restore functional metrics from LR images of squamous epithelial tissues using supervised and unsupervised deep autoencoding algorithms. The reversed unsupervised algorithm is applied to reduce the resolution of HR images to quantitatively assess the impact of LR imaging on metabolic information acquisition. Improved functional metrics extraction is expected to accelerate the clinical translation of novel non-invasive diagnostic solutions.

---

### 🔑 Keywords:
- Resolution enhancement
- Image restoration
- Redox ratio
- Deep learning
- Unsupervised machine learning
- Two-photon
- Label-free
- Morpho-functional analysis

---

### 👤 Biography:
**Tien Long Dinh** is a senior undergraduate student at Tufts University and a research assistant at the Georgakoudi Lab. His current work focuses on the development and investigation of image processing, object detection, and transformation algorithms for non-invasive biomedical diagnostics, including polarization-enhanced laparoscopy and high-resolution microscopic imaging.
