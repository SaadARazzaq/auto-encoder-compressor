# AutoEncoderCompressor: Neural Image Compression Framework

A deep learning-based image compression system utilizing Stacked Denoising Convolutional Autoencoders with advanced activation functions and up-sampling techniques.

The objective of this work is to reduce image storage footprint through a neural network-based compression pipeline. The core component is a Stacked Denoising Autoencoder (SDAE) enhanced with Parametric ReLU (PReLU) activation functions to improve gradient flow and a Sub-pixel layer for efficient, learnable up-sampling. Following training on the Flickr Image Dataset, the model's performance was quantified on the Kodak Image Dataset, yielding a 76% reconstruction accuracy, indicating potential for further optimization. For the compression stage, the encoder's latent representation is losslessly compressed using the Deflate algorithm. On 128x128 images, this pipeline achieves an average compression ratio of 89.92% relative to the original format, a 43.97% improvement over JPEG.

<img alt="image" src="https://github.com/user-attachments/assets/32693103-5182-4b78-9157-3ef487b724d9" />

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

<img width="1000" height="300" alt="image" src="https://github.com/user-attachments/assets/61453902-1597-46ac-b5c9-447e8fcf0d4e" />

## 🔬 Experimental Results

### Compression Efficiency Comparison

| Algorithm | Average Compression Rate | Improvement over JPEG |
|-----------|-------------------------|----------------------|
| JPEG | 43.07% | - |
| NeuroCompress | 89.92% | +43.97% |

### Detailed Performance Analysis

| Original Size (bytes) | Latent Representation (bytes) | Compressed Size (bytes) | Compression Time (s) | Decompression Time (s) | JPEG Rate (%) | NeuroCompress Rate (%) |
|----------------------|-------------------------------|-------------------------|---------------------|------------------------|---------------|----------------------|
| 33,799 | 11,487 | 3,070 | 0.0018 | 3.9577E-5 | 44.46 | 90.92 |
| 31,532 | 11,414 | 3,102 | 0.0016 | 4.3154E-5 | 43.83 | 90.16 |
| 30,957 | 11,323 | 3,421 | 0.0013 | 4.4107E-5 | 41.40 | 88.95 |
| 33,680 | 11,423 | 3,491 | 0.0012 | 4.3631E-5 | 42.61 | 89.63 |

### Performance Statistics

| Metric | Value |
|--------|-------|
| Average Compression Time | 1.47ms |
| Average Decompression Time | 42.62μs |
| Average JPEG Compression Rate | 43.07% |
| Average NeuroCompress Rate | 89.92% |

## 🏗️ System Architecture

```
Input Image → Encoder → Latent Representation → Deflate Compression
     ↓
Compressed Data → Deflate Decompression → Decoder → Reconstructed Image
```

## 🎯 Key Features

| Feature | Description |
|---------|-------------|
| Architecture | Stacked Denoising Convolutional Autoencoder |
| Compression Type | Non-end-to-end |
| Latent Compression | Deflate Algorithm |
| Training Dataset | Flickr Image Dataset |
| Evaluation Dataset | Kodak Image Dataset |

## 📈 Quality Metrics

| Metric | Value |
|--------|-------|
| Structural Similarity (SSIM) | High (Refer to comparison chart) |
| Reconstruction Accuracy | 76% |
| Compression Ratio | ~90% |

## 🔍 Technical Specifications

| Component | Technology |
|-----------|------------|
| Neural Network | Stacked Denoising Autoencoder |
| Activation | PReLU [2] |
| Up-sampling | Sub-pixel Layer [11] |
| Compression | Deflate Algorithm [9] |
| Training Data | Flickr Dataset [4] |
| Testing Data | Kodak Dataset [7] |

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
