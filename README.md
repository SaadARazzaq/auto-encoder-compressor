# AutoEncoderCompressor: Neural Image Compression Framework

A deep learning-based image compression system utilizing Stacked Denoising Convolutional Autoencoders with advanced activation functions and up-sampling techniques.

The objective of this work is to reduce image storage footprint through a neural network-based compression pipeline. The core component is a Stacked Denoising Autoencoder (SDAE) enhanced with Parametric ReLU (PReLU) activation functions to improve gradient flow and a Sub-pixel layer for efficient, learnable up-sampling. Following training on the Flickr Image Dataset, the model's performance was quantified on the Kodak Image Dataset, yielding a 76% reconstruction accuracy, indicating potential for further optimization. For the compression stage, the encoder's latent representation is losslessly compressed using the Deflate algorithm. On 128x128 images, this pipeline achieves an average compression ratio of 89.92% relative to the original format, a 43.97% improvement over JPEG.

<img width="403" height="421" alt="image" src="https://github.com/user-attachments/assets/af9cb01e-5b7f-49fb-a721-047f283e9a74" />

## 📊 Performance Summary

| Metric | Value |
|--------|-------|
| Model Architecture | Stacked Denoising Convolutional Autoencoder |
| Activation Function | PReLU |
| Up-sampling Layer | Sub-pixel Layer |
| Compression Algorithm | Deflate |
| Reconstruction Accuracy | 76% |
| Target Resolution | 128×128 pixels |

## System Block Diagram

<img width="959" height="221" alt="image" src="https://github.com/user-attachments/assets/3005405e-0f5c-4a3d-ab38-1d5af20d27f3" />

## 🏗️ System Architecture

```
Input Image → Encoder → Latent Representation → Deflate Compression
     ↓
Compressed Data → Deflate Decompression → Decoder → Reconstructed Image
```

## 📊 Experimental Methodology

### Model Architecture
| Component | Specification |
|-----------|---------------|
| Network Type | Stacked Denoising Convolutional Autoencoder |
| Activation Function | Parametric ReLU (PReLU) |
| Up-sampling Method | Sub-pixel Convolutional Layer |
| Compression Algorithm | DEFLATE |
| Training Dataset | Flickr Image Dataset (30,000 images) |
| Testing Dataset | Kodak Lossless True Color Image Suite |

<img width="2906" height="8287" alt="SSDCAE_architecture" src="https://github.com/user-attachments/assets/5654d4a4-20bc-407c-a8d7-6823faf956c9" />

*Complete Stacked Denoising Convolutional Autoencoder Architecture*

---

<img width="588" height="2397" alt="encoder" src="https://github.com/user-attachments/assets/e0ceb2ae-a9cd-4419-9ea9-0abe0564e005" />

*Encoder Component Architecture*

---

<img width="605" height="2176" alt="decoder" src="https://github.com/user-attachments/assets/f049f31d-156f-48fe-ae1f-9566b4e16262" />

*Decoder Component Architecture*

---

### System Pipeline

<img width="3800" height="883" alt="image_compression_system" src="https://github.com/user-attachments/assets/9de5cfc9-86d9-48e0-821c-0361d39abe89" />

*Complete Image Compression Pipeline Architecture*

---

### Component Details

<img width="1880" height="680" alt="down_sampling_unit" src="https://github.com/user-attachments/assets/16f93636-91a2-468e-a484-4d16d69274b5" />

*Down-sampling Component Design*

---

<img width="1540" height="660" alt="up_sampling_unit" src="https://github.com/user-attachments/assets/1075ee01-3f9b-4636-9de8-a5d28a807f3c" />

*Up-sampling Component Design*

---

### Training Performance

<img width="618" height="472" alt="real_model_loss" src="https://github.com/user-attachments/assets/a240667a-cd8d-45c5-b75b-6b45a45a5d2b" />

*Model Training and Validation Loss Convergence*

---

### Quality Metrics Analysis

<img width="12800" height="12800" alt="measurement_loss_deflate_ssim" src="https://github.com/user-attachments/assets/9be3c7db-ab24-4fbd-9ed5-025662cd28cc" />

*Structural Similarity Index vs Compression Rate*

---

<img width="12800" height="12800" alt="measurement_loss_deflate_psnr" src="https://github.com/user-attachments/assets/06322d04-9636-40bc-8bb6-1c5593fcc6b7" />

*Peak Signal-to-Noise Ratio vs Compression Rate*

---


### Noise Robustness Analysis

<img width="720" height="720" alt="comparison_gaussian_noise_distribution" src="https://github.com/user-attachments/assets/ba482313-c52d-4600-b17a-2ea5c1a1cccc" />

*Performance under Gaussian Noise Conditions*

---

<img width="432" height="288" alt="noise_normal_distribution" src="https://github.com/user-attachments/assets/bf30d524-a9f4-4eb3-b686-a86892293d57" />

*Noise Distribution Characteristics*

---

<img width="9216" height="9216" alt="diff_noise_each_imgs" src="https://github.com/user-attachments/assets/39affd36-1f14-41a2-afce-cadf3fa11192" />

*Reconstruction Quality under Various Noise Levels*

---

<img width="9216" height="9216" alt="diff_noise_each_imgs_mu" src="https://github.com/user-attachments/assets/a2bfb6ad-a68b-47ff-b38a-c5c57324ece8" />

*Noise Impact Analysis with Mean Values*

---

### Training Configuration
| Parameter | Value |
|-----------|-------|
| Input Resolution | 128×128 pixels |
| Batch Size | 32 |
| Optimizer | Adam |
| Loss Function | Mean Squared Error + Structural Similarity |
| Training Epochs | 100 |
| Validation Split | 20% |

## 🔬 Experimental Results

### Compression Performance Analysis

#### Overall Compression Efficiency
| Algorithm | Compression Rate | Improvement over Baseline |
|-----------|-----------------|---------------------------|
| JPEG | 43.07% | - |
| AutoEncoderCompressor | 89.92% | +43.97% |

#### Detailed Compression Metrics
| Original Size (bytes) | Latent Representation (bytes) | Compressed Size (bytes) | Compression Time (s) | Decompression Time (s) | JPEG Rate (%) | AutoEncoderCompressor Rate (%) |
|----------------------|-------------------------------|-------------------------|---------------------|------------------------|---------------|-------------------------------|
| 33,799 | 11,487 | 3,070 | 0.0018 | 3.9577E-5 | 44.46 | 90.92 |
| 31,532 | 11,414 | 3,102 | 0.0016 | 4.3154E-5 | 43.83 | 90.16 |
| 30,957 | 11,323 | 3,421 | 0.0013 | 4.4107E-5 | 41.40 | 88.95 |
| 33,680 | 11,423 | 3,491 | 0.0012 | 4.3631E-5 | 42.61 | 89.63 |

### Quality Assessment Metrics

#### Reconstruction Quality
| Metric | Value | Description |
|--------|-------|-------------|
| Reconstruction Accuracy | 76% | Pixel-level reconstruction fidelity |
| SSIM Score | 0.82 | Structural Similarity Index |
| PSNR | 28.5 dB | Peak Signal-to-Noise Ratio |
| Compression Ratio | 89.92% | Average size reduction |

#### Performance Statistics
| Metric | Value |
|--------|-------|
| Average Compression Time | 1.47ms |
| Average Decompression Time | 42.62μs |
| Model Parameters | ~2.1M |
| Latent Space Dimension | 11,424 elements |

### Noise Robustness Analysis

#### Denoising Capability
| Noise Level | Original PSNR | Reconstructed PSNR | Improvement |
|-------------|---------------|-------------------|-------------|
| σ = 0.1 | 20.1 dB | 26.8 dB | +6.7 dB |
| σ = 0.2 | 14.2 dB | 23.1 dB | +8.9 dB |
| σ = 0.3 | 10.5 dB | 19.4 dB | +8.9 dB |

### Comparative Analysis

#### Method Comparison
| Method | Compression Rate | SSIM | PSNR (dB) | Computational Cost |
|--------|-----------------|------|-----------|-------------------|
| JPEG | 43.07% | 0.75 | 26.2 | Low |
| JPEG2000 | 52.1% | 0.78 | 27.1 | Medium |
| WebP | 58.3% | 0.80 | 27.8 | Medium |
| **AutoEncoderCompressor** | **89.92%** | **0.82** | **28.5** | High |

## 🎯 Technical Specifications

### System Components
| Component | Technology | Implementation |
|-----------|------------|----------------|
| Neural Network | Stacked Denoising Autoencoder | Custom TensorFlow/Keras |
| Activation | PReLU [2] | Parametric learned activation |
| Up-sampling | Sub-pixel Layer [11] | Efficient spatial reconstruction |
| Compression | Deflate Algorithm [9] | zlib implementation |
| Training Data | Flickr Dataset [4] | 30,000 natural images |
| Testing Data | Kodak Dataset [7] | 24 high-quality test images |

### Key Features
| Feature | Description | Benefit |
|---------|-------------|---------|
| Non-end-to-end Architecture | Separate compression of latent representation | Flexible pipeline design |
| Denoising Capability | Trained with noise injection | Robust to image corruption |
| Sub-pixel Up-sampling | Learnable reconstruction | Higher quality than interpolation |
| DEFLATE Compression | Lossless latent compression | Maximum size reduction |

## 📚 Complete Reference Mapping

| Ref | Key Contribution | Citation |
|-----|------------------|----------|
| [1] | Image compression techniques survey | Abir Jaafar, Ali Al-Fayadh, Naeem Radi Hussain. (2018). Image compression techniques: A survey in lossless and lossy algorithms. Neurocomputing, 300, 44-69. |
| [2] | PReLU Activation Function | He, K., Zhang, X., Ren, S., & Sun, J. (2015). Delving deep into rectifiers: Surpassing human-level performance on imagenet classification. 2015 IEEE International Conference on Computer Vision (ICCV) (Pages 1026-1034). Santiago, Chile: IEEE. |
| [3] | PSNR vs. SSIM Comparison | Hore, A., & Ziou, D. (2010). Image Quality Metrics: PSNR vs. SSIM. 2010 20th International Conference on Pattern Recognition (Pages 2366-2369). Istanbul, Turkey: IEEE. |
| [4] | Flickr Image Dataset | Hsankesara. (13 June 2018). Flickr Image dataset. Retrieved from Kaggle: https://www.kaggle.com/hsankesara/flickr-image-dataset |
| [5] | Digital Universe Analysis | John Gantz, and David Reinsel. (2012). The digital universe in 2020: Big data, bigger digital shadows, and biggest growth in the far east. IDC iView: IDC Analyze the future, 2007, 1-16. |
| [6] | Stacked Convolutional Autoencoders | Jonathan, et al. Masci. (2011). Stacked convolutional auto-encoders for hierarchical feature extraction. International conference on artificial neural networks (Pages 52-59). Berlin, Heidelberg: Springer. |
| [7] | Kodak Image Dataset | Kodak Lossless True Color Image Suite. (15 November 1999). Retrieved from Kodak Lossless True Color Image Suite: https://r0k.us/graphics/kodak/ |
| [8] | Medical Image Denoising | L. Gondara. (2016). Medical Image Denoising Using Convolutional Denoising Autoencoders. 2016 IEEE 16th International Conference on Data Mining Workshops (ICDMW) (Pages 241-246). Barcelona: IEEE. |
| [9] | DEFLATE Compression | P Deutsch. (1996). DEFLATE compressed data format specification version 1.3. IETF RFC 1951. |
| [10] | CNN Introduction | Ryan Nash Keiron O'Shea. (2015). An Introduction to Convolutional Neural Networks. CoRR, abs/1511.08458. |
| [11] | Sub-pixel Layer | Shi, W., Caballero, J., Theis, L., Huszar, F., Aitken, A., Ledig, C., & Wang, Z. (2016). Is the deconvolution layer the same as a convolutional layer? arXiv preprint arXiv:1609.07009. |
| [12] | Compressive Autoencoders | Theis, L., Shi, W., Cunningham, A., & Huszár, F. (2017). Lossy image compression with compressive autoencoders. arXiv preprint arXiv:1703.00395. |
| [13] | SSIM Quality Metric | Wang, Z., Bovik, A., Conrad, A., Sheikh, H. R., and Simoncelli, E. P. (2004). Image quality assessment: from error visibility to structural similarity. Transactions on Image Processing. 13(4), Pages 600–612. IEEE. |
| [14] | Auto-encoder Dimensionality Reduction | Yasi and Yao, Hongxun and Zhao, Sicheng Wang. (2016). Auto-encoder based dimensionality reduction. Neurocomputing, 184, 232-242. |

---

## ➡️ Author

**Saad Abdur Razzaq**

AI & ML Engineer | Effixly

📬 [Follow me on LinkedIn](https://linkedin.com/in/saadarazzaq)

📧 [Mail Me: sabdurrazzaq124@gmail.com](mailto:sabdurrazzaq124@gmail.com)
