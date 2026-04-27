# Skin Cancer Classification using Deep Learning

  A deep learning approach for binary classification of dermoscopic images to distinguish melanoma from benign nevi (moles).

  ## Problem Statement

  Skin cancer is one of the most common cancers worldwide, with melanoma being the deadliest form. Early detection significantly improves survival rates, yet visual diagnosis by dermatologists can be subjective and error-prone. This project develops a convolutional neural network (CNN) pipeline to assist in the automated classification of skin lesions from dermoscopic images.

  ## Dataset

  This project uses dermoscopic images for binary classification:

  - **Classes**: MEL (Melanoma) and NV (Nevus/Benign)
  - **Training set**: 6,426 images (3,213 per class)
  - **Validation set**: 1,252 images (626 per class)
  - **Image format**: RGB dermoscopic images
  - **Preprocessing**: Images resized and normalized using dataset-specific statistics

  The dataset is balanced, eliminating the need for class weighting or oversampling techniques.

  ## Methodology

  ### Model Architectures

  The project explores multiple architectures with increasing complexity:

  1. **SimpleCNN**: Baseline convolutional network with two conv layers and one fully connected layer
  2. **BatchNorm CNN**: SimpleCNN enhanced with batch normalization for training stability
  3. **Residual CNN**: Incorporates skip connections to improve gradient flow
  4. **VGG-16/VGG-19**: Pre-trained ImageNet models with frozen feature extractors and custom classifiers
  5. **DINOv2**: State-of-the-art vision transformer with self-supervised pre-training

  ### Data Augmentation

  To improve generalization and reduce overfitting:

  - Random horizontal and vertical flips
  - Random rotation (up to 30°)
  - Color jitter (brightness, contrast, saturation, hue)
  - Random resized cropping (scale 0.8–1.0)

  ### Training Configuration

  - **Optimizer**: Adam with learning rates tested from 1e-5 to 1e-2
  - **Loss function**: Binary Cross-Entropy with Logits
  - **Batch size**: 32
  - **Epochs**: 10 per experiment
  - **Early stopping**: Best model saved based on validation accuracy

  ## Evaluation Metrics

  - **Accuracy**: Overall classification correctness
  - **Precision**: Ratio of true positives to predicted positives
  - **Recall (Sensitivity)**: Ratio of true positives to actual positives
  - **F1-Score**: Harmonic mean of precision and recall
  - **ROC-AUC**: Area under the receiver operating characteristic curve

  ## Results

  | Model | Validation Accuracy |
  |-------|---------------------|
  | SimpleCNN (no augmentation) | 83.4% |
  | SimpleCNN (with augmentation) | 84.9% |
  | BatchNorm CNN | 85.1% |
  | Residual CNN | 85.2% |
  | VGG-16 (transfer learning) | ~86% |
  | DINOv2 (fine-tuned) | ~87% |

  *Note: Results may vary slightly between runs due to stochastic training.*

  ## How to Run

  1. Clone the repository:
     ```bash
     git clone https://github.com/yourusername/skin-cancer-classification.git
     cd skin-cancer-classification

  2. Install dependencies:
  pip install -r requirements.txt
  3. Place your dataset in the data/ directory with the following structure:
  data/
  ├── train/
  │   ├── MEL/
  │   └── NV/
  └── val/
      ├── MEL/
      └── NV/
  4. Open and run the Jupyter notebook:
  jupyter notebook notebooks/skin_cancer_classification.ipynb

  Limitations

  - Binary classification only: The model distinguishes melanoma from benign nevi but does not classify other skin lesion types
  - Dataset scope: Performance may vary on images from different dermoscopes or lighting conditions
  - No clinical validation: Results have not been validated in a clinical setting
  - Computational requirements: Transfer learning models (especially DINOv2) require GPU acceleration

  Ethical Considerations

  This project is intended for educational and research purposes only and should not be used for clinical diagnosis.

  Important disclaimers:

  - Not a medical device: This model is not FDA-approved or clinically validated
  - Human oversight required: Any deployment must include review by qualified dermatologists
  - Bias concerns: Model performance may vary across different skin tones and demographic groups; further validation on diverse datasets is essential
  - False negatives risk: Missing a melanoma diagnosis can have severe consequences; the model should only be used as a supplementary screening tool
  - Patient privacy: When working with medical images, ensure compliance with HIPAA, GDPR, and other applicable regulations

  Responsible AI in healthcare requires transparency, rigorous validation, and collaboration with medical professionals before any clinical application.

  Technologies Used

  - Python 3.8+
  - PyTorch
  - torchvision
  - NumPy
  - Matplotlib
  - scikit-learn
