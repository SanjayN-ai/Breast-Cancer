# 🔬 Breast Cancer Classification using CNN

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.18-orange?logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?logo=keras)
![License](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-yellow?logo=googlecolab)

A deep learning project that classifies breast histopathology image patches as **Benign** or **Malignant** using a custom Convolutional Neural Network (CNN) called **CancerNet**.

---

## 📌 Problem Statement

Breast cancer is one of the most common cancers worldwide. Early and accurate detection is critical for improving survival rates. Pathologists examine microscopic tissue images (histopathology images) to detect cancer — a time-consuming and error-prone process.

This project automates that classification using a CNN trained on thousands of real histopathology image patches.

---

## 📂 Dataset

- **Source:** [Breast Histopathology Images — Kaggle](https://www.kaggle.com/datasets/paultimothymooney/breast-histopathology-images)
- **Size:** ~3.1 GB
- **Total Images:** 48,422 PNG image patches (50×50 pixels)

| Class | Label | Count |
|-------|-------|-------|
| Benign (non-cancerous) | 0 | 36,511 |
| Malignant (cancerous) | 1 | 11,912 |

---

## 🧠 Model Architecture — CancerNet

A custom Sequential CNN built with Keras:

```
Input (50x50x3)
    ↓
Conv2D(32, 3x3, ReLU)
    ↓
MaxPooling2D(2x2)
    ↓
Conv2D(64, 3x3, ReLU)
    ↓
MaxPooling2D(2x2)
    ↓
Flatten
    ↓
Dense(128, ReLU)
    ↓
Dropout(0.5)
    ↓
Dense(2, Softmax)  →  Benign / Malignant
```

- **Optimizer:** Adam
- **Loss Function:** Categorical Crossentropy
- **Epochs:** 10
- **Batch Size:** 32

---

## ⚙️ How It Works

1. **Data Download** — Dataset downloaded from Kaggle using the Kaggle API
2. **Data Organization** — Images sorted into `data/0` (benign) and `data/1` (malignant) folders
3. **Preprocessing** — Images resized to 50×50, pixel values normalized to [0, 1]
4. **Train/Test Split** — 80% training, 20% testing
5. **Model Training** — CancerNet trained for 10 epochs on GPU (Tesla T4)
6. **Evaluation** — Confusion matrix and classification report generated
7. **Model Saving** — Trained model saved as `CancerNet.h5`

---

## 📊 Results

| Metric | Value |
|--------|-------|
| **Test Accuracy** | **85.54%** |
| Benign Precision | 87% |
| Benign Recall | 95% |
| Benign F1-Score | 0.91 |
| Malignant Precision | 78% |
| Malignant Recall | 56% |
| Malignant F1-Score | 0.66 |

### Confusion Matrix

|  | Predicted Benign | Predicted Malignant |
|--|-----------------|---------------------|
| **Actual Benign** | 6954 ✅ | 366 ❌ |
| **Actual Malignant** | 1034 ❌ | 1331 ✅ |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.11 | Programming Language |
| TensorFlow 2.18 | Deep Learning Framework |
| Keras | Model Building |
| OpenCV (cv2) | Image Loading & Resizing |
| NumPy | Array Operations |
| scikit-learn | Train/Test Split, Metrics |
| Matplotlib | Visualization |
| Google Colab | Cloud GPU Environment |
| NVIDIA Tesla T4 | GPU Acceleration |

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/SanjayN-ai/Breast-Cancer.git
cd Breast-Cancer
```

### 2. Open in Google Colab
Upload `Breast_Cancer_Classification.ipynb` to [Google Colab](https://colab.research.google.com/)

### 3. Setup Kaggle API
- Download your `kaggle.json` from [Kaggle Account Settings](https://www.kaggle.com/settings)
- Upload it when prompted in the notebook

### 4. Run All Cells
Run cells sequentially — the notebook will:
- Download and organize the dataset
- Train the CancerNet model
- Evaluate and display results
- Save the model as `CancerNet.h5`

---

## 📁 Project Structure

```
Breast-Cancer/
│
├── Breast_Cancer_Classification.ipynb   # Main notebook
├── README.md                            # Project documentation
└── LICENSE                              # MIT License
```

---

## ⚠️ Limitations

- **Class Imbalance:** Dataset has ~3x more benign than malignant images, leading to lower recall for malignant class
- **Simple Architecture:** A basic CNN is used; transfer learning models (ResNet, EfficientNet) could improve performance
- **No Data Augmentation:** Adding flips/rotations could improve generalization

---

## 🔮 Future Improvements

- [ ] Handle class imbalance using `class_weight` or oversampling
- [ ] Add data augmentation (flips, rotations, zoom)
- [ ] Experiment with transfer learning (EfficientNetB0, ResNet50)
- [ ] Deploy model as a web app using Streamlit or Flask
- [ ] Save model in `.keras` format instead of `.h5`

---

## 👤 Author

**Sanjay N**  
[![GitHub](https://img.shields.io/badge/GitHub-SanjayN--ai-black?logo=github)](https://github.com/SanjayN-ai)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
