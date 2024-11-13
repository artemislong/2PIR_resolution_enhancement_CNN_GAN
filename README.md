# 📝 Label-Free, Two-Photon Image Resolution Enhancement Using a Deep-Learning Autoencoder Algorithm

---

### 👥 Authors:
- **Tien Long Dinh**¹*, **Christopher M. Polleys**¹, **Nilay Vora**¹, **Hong-Thao Thieu**², **Elizabeth Genega**³, and **Irene Georgakoudi**¹⁴  
  - ¹ Department of Biomedical Engineering, Tufts University, Medford, MA, USA  
  - ² Department of Obstetrics and Gynecology, Tufts Medical Center, Boston, MA, USA  
  - ³ Department of Pathology and Laboratory Medicine, Tufts Medical Center, Boston, MA, USA  
  - ⁴ Cell, Developmental, and Molecular Biology Program, Tufts University, Boston, MA, USA  

---
![image](https://github.com/user-attachments/assets/cb2a1984-322d-4b45-9fe8-466163118310)

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
