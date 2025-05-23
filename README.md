# Multimodal Image Reconstruction

This project proposes a semantic communication framework for image transmission. Instead of sending raw image data, we transmit a compressed representation composed of a natural language caption and a structural control image (such as line art or edge map). At the receiver's end, Stable Diffusion and ControlNet are used to reconstruct the original image with high fidelity.

## Key Features

- High-resolution image reconstruction from compressed data
- Uses Stable Diffusion conditioned on text and structural input
- Integration of ControlNet for structural guidance
- Evaluation using PSNR, MSE, SSIM, and LPIPS
- Caption + Line Art consistently outperforms other combinations

## Motivation

Conventional image transmission requires large bandwidth and transmits redundant data. Semantic communication focuses on transmitting only the meaningful parts of an image (its structure and semantic content). This method is particularly useful in bandwidth-constrained scenarios such as mobile imaging and remote sensing.

## Methodology

### Encoder

- Generate a textual caption summarizing the image
- Create a 128x128 structural control image using:
  - Canny Edge detection
  - Line art rendering
  - Depth estimation

### Decoder

- Use Stable Diffusion to reconstruct the image from:
  - Textual caption (semantic prompt)
  - Structural control image (for spatial layout)
- ControlNet ensures structural consistency

## Evaluation

The system was evaluated across four commonly used image similarity metrics:

- **PSNR** (Peak Signal-to-Noise Ratio)
- **MSE** (Mean Squared Error)
- **SSIM** (Structural Similarity Index)
- **LPIPS** (Learned Perceptual Image Patch Similarity)

The combination of **Caption + Line Art** consistently yielded the best results across all metrics, demonstrating the effectiveness of using structured semantic compression for high-quality image reconstruction.

## Project Structure
.
├── models/                # Model weights and configurations
├── data/                  # Input samples and control images
├── scripts/               # Training and inference scripts
├── results/               # Output visualizations
├── utils/                 # Supporting code
├── README.md              # Project documentation
└── report.pdf             # Detailed project report

## Key Insights

- Semantic communication enables efficient image transmission by focusing on meaning and structure.
- The proposed method shows strong performance in terms of both perceptual quality and structural consistency.
- Line art provides more informative guidance than other control maps (such as edges or depth), leading to better reconstructions when combined with captions.

## Applications

This method can be applied in areas where bandwidth is limited but visual fidelity is important, such as:

- Remote sensing
- Telemedicine
- Mobile imaging
- Augmented and virtual reality systems
