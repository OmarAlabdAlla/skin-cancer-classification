# Skin Cancer Classification (Deep Learning)

Deep learning-based classification of skin lesions (melanoma vs benign) using dermoscopic images.

## Problem

Skin cancer is one of the most common cancers worldwide, with melanoma being the most dangerous form. Early detection is critical. This project explores deep learning models to classify skin lesions based on image data.

## Dataset

* Binary classification: MEL (melanoma) vs NV (benign)
* Training set: 6,426 images
* Validation set: 1,252 images
* Images resized and normalized before training

## Approach

### Models

* Baseline CNN
* CNN with batch normalization
* Residual CNN
* Transfer learning using pre-trained models

### Data Augmentation

* Random flips
* Rotation
* Color jitter
* Random cropping

### Training

* Optimizer: Adam
* Loss: Binary Cross-Entropy
* Batch size: 32
* Epochs: 10

## Results

| Model             | Validation Accuracy |
| ----------------- | ------------------- |
| SimpleCNN         | 83–85%              |
| BatchNorm CNN     | ~85%                |
| Residual CNN      | ~85%                |
| Transfer Learning | ~86–87%             |

(See notebook for full details)

## How to Run

```bash
git clone https://github.com/yourusername/skin-cancer-classification.git
cd skin-cancer-classification
pip install -r requirements.txt
jupyter notebook skin_cancer_classification.ipynb
```

## Limitations

* Binary classification only
* Performance may vary on different datasets
* Not clinically validated

## Ethical Considerations

This project is for educational purposes only and must not be used for medical diagnosis.

* Requires human medical oversight
* Risk of false negatives
* Potential bias across populations

## Technologies

* Python
* PyTorch
* NumPy
* Matplotlib
* scikit-learn
