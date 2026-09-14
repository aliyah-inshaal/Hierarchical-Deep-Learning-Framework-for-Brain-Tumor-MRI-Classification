# Leakage-Safe Hierarchical Brain Tumor MRI Classification

A reproducible deep learning framework for **multi-class brain tumor classification from MRI images** using a **two-stage hierarchical classification approach**.

Instead of directly classifying all classes in a single model, this project introduces a hierarchical pipeline:

1. **Stage 1: Binary Router**

   * Separates normal MRI scans from abnormal tumor scans.
   * Prevents normal images from competing with multiple tumor subtypes.

2. **Stage 2: Abnormal-Only Expert Classifier**

   * Classifies abnormal scans into **14 different brain tumor categories**.
   * Focuses model capacity only on tumor subtype discrimination.

The project also includes leakage-safe dataset splitting, baseline comparisons, ablation studies, explainability analysis, and external validation.


# 📄 Publication / Conference Presentation

This work was presented at:

**3rd International Conference on Emerging Trends and Applications in Artificial Intelligence (ICETAI 2026)**

The study explores a hierarchical deep learning approach for automated brain tumor MRI classification with emphasis on robust evaluation, explainability, and generalization.

# 🏗️ Model Architecture

## Stage 1: Normal-Abnormal Router

**Architecture:**

* ResNet18

**Task:**

Binary classification:

| Label | Class    |
| ----- | -------- |
| 0     | Normal   |
| 1     | Abnormal |

The router acts as a filtering mechanism that forwards only abnormal scans to the tumor classifier.

---

## Stage 2: Tumor Expert Classifier

**Architecture:**

* EfficientNetB0

**Task:**

14-class abnormal tumor classification.

The Normal class is removed from this stage so the model focuses entirely on distinguishing tumor subtypes.

---

# 📊 Experiments

The project evaluates multiple components:

## 1. Hierarchical Pipeline Evaluation

Complete system evaluation:

```
Router + Expert Classifier
```

Metrics include:

* Accuracy
* Precision
* Recall
* Macro F1-score
* Weighted F1-score
* Confusion Matrix

---

## 2. Flat Classification Baselines

Comparison against single-stage classifiers:

* ResNet50
* DenseNet121
* EfficientNetB0

These models directly classify all 15 classes without hierarchy.

---

## 3. Ablation Studies

To measure contribution of each component:

### Without Router

All images are directly classified by the expert model.

### Without Expert Specialization

Comparison against non-hierarchical alternatives.

---

# 🔍 Explainability Analysis

The project integrates **Grad-CAM visualization** to understand model decisions.

Grad-CAM highlights image regions contributing to predictions and helps analyze:

* Correct predictions
* Incorrect predictions
* Class-specific attention patterns

---

# 🌍 External Validation

Generalization is evaluated using an external Figshare brain tumor dataset.

The evaluation investigates whether the learned representations transfer beyond the original dataset.

---

# 🛠️ Technologies Used

## Deep Learning

* PyTorch
* Torchvision
* EfficientNet
* ResNet

## Data Processing

* Python
* NumPy
* Pandas
* OpenCV
* PIL

## Machine Learning

* Scikit-learn

## Visualization

* Matplotlib
* Grad-CAM


# 📈 Evaluation Metrics

The project evaluates models using:

* Accuracy
* Precision
* Recall
* Macro F1-score
* Weighted F1-score
* Confusion Matrix

Additional analysis:

* Ablation comparison
* Grad-CAM interpretation
* External dataset validation


# 📚 Dataset

The project uses a publicly available on kaggle 14 class brain tumor MRI dataset containing:

* Normal MRI images
* Multiple tumor categories

External validation is performed using the Figshare Brain Tumor Dataset.

