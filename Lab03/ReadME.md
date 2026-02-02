# VAE vs. Autoencoder on MNIST

This repository contains a PyTorch implementation comparing a Variational Autoencoder (VAE) and a standard Autoencoder (AE) trained on the MNIST dataset. The goal is to demonstrate the impact of the Kullback-Leibler (KL) divergence term in VAEs on sample generation and the structure of the latent space.

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Results and Analysis](#results-and-analysis)
- [Generated Samples](#generated-samples)

## Project Overview

This project implements two types of generative models: a Variational Autoencoder (VAE) and a standard Autoencoder (AE). Both models are built with a simple feed-forward architecture and trained on the MNIST handwritten digits dataset. The core difference lies in their loss functions: the VAE incorporates a KL divergence term to encourage a continuous and disentangled latent space, while the AE only uses reconstruction loss.

The notebook walks through:
1.  Defining the VAE architecture.
2.  Implementing VAE and AE specific loss functions.
3.  Training both models.
4.  Comparing generated samples from both models.
5.  Visualizing and comparing their 2D latent spaces.

## Features

*   **PyTorch Implementation**: Models built using PyTorch for flexibility and performance.
*   **MNIST Dataset**: Standard dataset for image generation tasks.
*   **VAE with KL Divergence**: Training a VAE with reconstruction loss and KL divergence.
*   **Autoencoder (AE) without KL Divergence**: Training a similar architecture as an AE using only reconstruction loss.
*   **Sample Generation**: Demonstrates image generation capabilities of both models.
*   **Latent Space Visualization**: Visualizes the 2D latent space learned by both models, highlighting the effect of KL divergence.
*   **Output Saving**: Saves generated images and zips them for easy download.

## Setup Instructions

To run this notebook, you need to have Python and the following libraries installed. It's recommended to use a virtual environment.

1.  **Clone the repository (if applicable):**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```

2.  **Install dependencies:**
    ```bash
    pip install torch torchvision matplotlib
    ```

3.  **For Google Colab:**
    No specific setup is needed beyond opening the `.ipynb` file in Colab. The necessary libraries are usually pre-installed, and the MNIST dataset will be downloaded automatically.

## Usage

1.  **Open the notebook:** Open `vae_ae_mnist_comparison.ipynb` (or similar name) in your preferred Jupyter environment (e.g., Jupyter Lab, VS Code, Google Colab).
2.  **Run all cells:** Execute all cells sequentially. The notebook will:
    *   Load the MNIST dataset.
    *   Define and train the VAE model (with KL divergence).
    *   Define and train the Autoencoder model (without KL divergence).
    *   Generate and display sample images from both models.
    *   Visualize the latent space for both models.
    *   Save 50 generated images from each model into `outputs/vae_images` and `outputs/ae_images`.
    *   Create `vae_generated_images.zip` and `ae_generated_images.zip` in the root directory.

## Results and Analysis

### Training Loss

The training logs will show the loss progression for both VAE and AE models. The VAE loss includes both reconstruction and KL divergence terms, while the AE loss only accounts for reconstruction.

### Sample Generation

*   **VAE Generated Images (With KL)**: Samples from the VAE tend to be more diverse and can generate novel images not seen in the training data, often exhibiting smoother transitions between digits. This is due to the regularized latent space. The generated samples are generally recognizable as MNIST digits.
*   **AE Generated Images (Without KL)**: Samples from the AE tend to be less diverse and might appear more like blurred or averaged versions of training data. Without the KL term, the latent space can become sparse or discontinuous, making sampling from it less effective for generating meaningful new data.

### Latent Space Visualization

*   **Latent Space WITH KL (VAE)**: The plot of the 2D latent space for the VAE typically shows a more structured and continuous distribution, often resembling a Gaussian distribution (a result of the KL divergence pushing the latent distribution towards a prior). Different digit clusters might be visible, but they are generally well-interspersed without large gaps, allowing for smooth interpolations.
*   **Latent Space WITHOUT KL (Autoencoder)**: The latent space for the AE often appears more scattered, with distinct, disconnected clusters for each digit. There might be large empty regions between clusters, making interpolation (and thus generation of meaningful novel samples) challenging, as sampling from these empty regions yields poor results.

This comparison clearly illustrates how the KL divergence term in VAEs forces the latent space to be continuous and allows for more effective generation of new, diverse samples, unlike a standard autoencoder which primarily focuses on reconstruction accuracy.

## Generated Samples

After running the notebook, you will find two `.zip` files:
*   `vae_generated_images.zip`: Contains 50 images generated by the VAE.
*   `ae_generated_images.zip`: Contains 50 images generated by the Autoencoder.
