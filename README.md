# 🩺 Breast Cancer Image Classification with ResNet50

This project is a binary image classifier that distinguishes between **healthy** and **sick** tissue samples from histopathological images using a fine-tuned **ResNet50** model in PyTorch.

## 📁 Dataset

- Images are organized in the `train/` folder with two subfolders:
  - `train/Healthy/`
  - `train/Sick/`
- The original dataset is split into:
  - 80% training
  - 20% validation
  - Seperate testing data


## 🧠 Model Architecture

- Base model: `ResNet50` (pretrained on ImageNet)
- Final FC layer modified to output a single logit for binary classification
- Loss function: `BCEWithLogitsLoss`
- Optimizer: `Adam`
- Scheduler: `StepLR`

## 🔁 Training Details

- Image size: `224x224`
- Batch size: `32`
- Data augmentation:
  - Random horizontal flip
  - Random rotation
- Normalization: Mean and std set to `[0.5, 0.5, 0.5]`
- Early stopping with patience = `5`
- Training runs for max `20 epochs`

## ✅ Evaluation

- Accuracy is calculated on the held-out test set
- Test predictions are thresholded at 0.5 after applying sigmoid
- Final test accuracy is printed after training