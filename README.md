# Automatic Detection of Invasive Ductal Carcinoma in Whole Slide Images

![Project Banner](banner_image_url) <!-- Replace with your project's banner image URL -->

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)
- [Contact](#contact)

## Introduction

Welcome to the **Automatic Detection of Invasive Ductal Carcinoma (IDC) in Whole Slide Images (WSI)** project. This project leverages deep learning, specifically Convolutional Neural Networks (CNNs), to automate the detection and analysis of IDC regions in digital histopathology slides of breast cancer. By automating this process, we aim to assist pathologists in improving diagnostic accuracy and efficiency.

## Features

- **Deep Learning-Based Detection**: Utilizes CNNs to identify IDC regions within WSIs.
- **High Accuracy**: Achieves competitive F-measure and Balanced Accuracy compared to traditional handcrafted feature approaches.
- **Scalable Processing**: Capable of handling large WSI datasets efficiently.
- **Visual Probability Maps**: Generates probability maps highlighting IDC regions for easy visualization and analysis.
- **Reproducible Results**: Ensures consistency across different datasets and annotations.

## Architecture

The project follows a three-step framework:

1. **Image Patch Sampling**:
    - Divides each WSI into non-overlapping patches (100x100 pixels).
    - Filters out patches with predominantly fatty tissue or slide background.
    - Labels patches as positive (IDC) if ≥80% overlaps with annotated IDC regions, else negative.

2. **Convolutional Neural Networks (CNN)**:
    - Implements a 3-layer CNN architecture:
        - **Convolutional Layers**: Extract hierarchical features from image patches.
        - **Pooling Layers**: Reduce dimensionality and retain essential features.
        - **Fully-Connected Layer**: Captures complex feature relationships.
    - Trained using stochastic gradient descent with optimized parameters.

3. **IDC Probability Map Generation**:
    - Assigns probability scores to each patch indicating the likelihood of IDC presence.
    - Compiles these scores into a comprehensive probability map over the entire WSI.

![Architecture Diagram](architecture_diagram_url) <!-- Replace with your project's architecture diagram URL -->

## Installation

### Prerequisites

- Python 3.7 or higher
- [TensorFlow](https://www.tensorflow.org/) or [PyTorch](https://pytorch.org/)
- [OpenSlide](https://openslide.org/) for WSI processing
- Other dependencies listed in `requirements.txt`

### Steps

1. **Clone the Repository**
    ```bash
    git clone https://github.com/yourusername/idc-detection-wsi.git
    ```

2. **Create a Virtual Environment**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```

## Usage

### Data Preparation

1. **Preprocessing**:
    - Convert WSIs to a suitable format (e.g., TIFF).
    - Downsample images if necessary to manage computational load.

### Training the Model

1. **Configure Training Parameters**:
    - Edit the `config.yaml` file to set parameters such as learning rate, batch size, number of epochs, etc.

2. **Monitor Training**:
    - Use TensorBoard or similar tools to visualize training progress and performance metrics.

### Inference

1. **View Probability Maps**
    - The generated probability maps highlight regions with high likelihood of IDC presence.

### Evaluation

1. **Review Metrics**
    - The script will output performance metrics such as Precision, Recall, F-measure, and Balanced Accuracy.
### Description

The dataset comprises digitized histopathology slides from **162 patients diagnosed with IDC**. The slides are obtained from reputable institutions and are annotated by expert pathologists to provide ground truth for IDC regions.

### Structure

```
data/
├── X.npy
├── Y.npy
```

### Annotation

- **Manual Annotation**: Expert pathologists manually delineate IDC regions using software like ImageScope.
- **Patch Labeling**: Patches are labeled based on the overlap with annotated IDC regions (≥80% overlap for positive labels).

## Results

The CNN-based approach demonstrates superior performance compared to traditional handcrafted feature methods:

- **F-measure**: 71.80%
- **Balanced Accuracy (BAC)**: 84.23%
- **Precision**: 65.40%
- **Recall/Sensitivity**: 79.60%
- **Specificity**: 88.86%

These results highlight the effectiveness of deep learning in accurately detecting IDC regions within WSIs, offering significant improvements over manual feature extraction techniques.

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. **Fork the Repository**
2. **Create a Feature Branch**
    ```bash
    git checkout -b feature/YourFeature
    ```
3. **Commit Your Changes**
    ```bash
    git commit -m "Add YourFeature"
    ```
4. **Push to the Branch**
    ```bash
    git push origin feature/YourFeature
    ```
5. **Open a Pull Request**

Please ensure that your contributions adhere to the project's coding standards and include appropriate tests.

## License

This project is licensed under the [MIT License](LICENSE).