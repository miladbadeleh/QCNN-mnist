# Quantum Convolutional Neural Network (QCNN) for MNIST Classification

## Overview
This project implements a Quantum Convolutional Neural Network (QCNN) to classify handwritten digits from the MNIST dataset, specifically distinguishing between digits 3 and 6. The implementation uses TensorFlow Quantum (TFQ) and Cirq to create and train a quantum machine learning model.

## Key Components

### 1. Data Preparation
- **Dataset Loading**: The MNIST dataset is loaded and normalized to values between 0.0 and 1.0
- **Filtering**: Only digits 3 and 6 are selected for binary classification
- **Image Resizing**: Images are downsampled from 28×28 to 4×4 pixels to make them suitable for quantum processing
- **Binarization**: Pixel values are thresholded at 0.5 to create binary images

### 2. Quantum Data Encoding
- **Circuit Creation**: Each 4×4 binary image is encoded into a quantum circuit where a qubit is activated (using an X gate) if the corresponding pixel value is 1
- **Contradiction Removal**: Images that could be interpreted as both 3 and 6 are removed to ensure clean training data

### 3. Quantum Model Architecture
- **Circuit Design**: Uses a 4×4 grid of qubits plus one readout qubit
- **Layers**:
  - XX (entangling) gates
  - ZZ (entangling) gates
- **Readout**: Final measurement is performed on the readout qubit using a Z operation

### 4. Training
- **Loss Function**: Hinge loss (suitable for binary classification)
- **Optimizer**: Adam optimizer
- **Metrics**: Custom hinge accuracy metric

### 5. Evaluation
- Trained for 10 epochs
- Achieves ~90.8% test accuracy

## Requirements
- Python 3.x
- TensorFlow 2.15.0
- TensorFlow Quantum 0.7.3
- Cirq 1.3.0
- NumPy
- Matplotlib
- Seaborn

## Usage
- Run the Jupyter notebook QCNN-mnist.ipynb
- The notebook will:
- Load and preprocess the MNIST data
- Build the quantum model
- Train the QCNN
- Evaluate performance

## Results
The model achieves approximately 90.8% accuracy on the test set for distinguishing between digits 3 and 6.

## Installation
```bash
pip install tensorflow==2.15.0 tensorflow-quantum==0.7.3 cirq==1.3.0 numpy matplotlib seaborn

