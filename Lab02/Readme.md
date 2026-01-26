
---

# GAN for MNIST Image Generation

## Objective

This project implements a Generative Adversarial Network (GAN) to generate synthetic handwritten digit images using the MNIST dataset. The model is trained for 50 epochs, generates sample images during training, produces 100 final images, and evaluates them using a pre-trained CNN classifier.

---

## Dataset

The MNIST dataset of handwritten digits (0–9) is used.

* Images reshaped to `(28, 28, 1)`
* Pixel values normalized to the range `[-1, 1]`

---

## GAN Architecture

### Generator

* Input noise vector of size `100`
* Dense layer projected to `7 × 7 × 256`
* Batch Normalization and LeakyReLU
* Reshape to `(7, 7, 256)`
* Conv2DTranspose layers to upsample
* Final output: `(28, 28, 1)` with `tanh` activation

### Discriminator

* Input shape `(28, 28, 1)`
* Two Conv2D layers with LeakyReLU and Dropout
* Flatten layer
* Final Dense layer with 1 output (logit)

---

## Training Details

* Epochs: `50`
* Batch size: `128`
* Noise dimension: `100`
* Learning rate: `0.0002`
* Optimizer: Adam
* Loss function: Binary Cross-Entropy (from logits)

Sample images are saved every 5 epochs.

---

## Results

* 100 final images generated after training
* Images saved in `final_generated_images/`
* Intermediate samples saved in `generated_samples/`

---

## Evaluation

A CNN classifier trained on MNIST was used to evaluate generated images.

* Validation accuracy on MNIST test set: ~98.76%

### Predicted Label Distribution (100 Images)

0: 9, 1: 10, 2: 9, 3: 13, 4: 12,
5: 6, 6: 11, 7: 10, 8: 10, 9: 10

---

## Conclusion

The GAN successfully generates diverse and recognizable MNIST digits. The balanced label distribution indicates that the model avoids mode collapse and produces varied outputs.

---

