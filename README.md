# SageMaker - Scikit-Learn Custom Script Project

This repository demonstrates how to build, train, and deploy a machine learning model on **AWS SageMaker** using a custom **Scikit-Learn (SKLearn)** script.  
It covers the full workflow — from dataset preparation and splitting to training, testing, and deployment.

---

## 📂 Project Structure

```
.
├── script.py                                         # Custom training script for SageMaker
├── Tutorial - 1 Sagemaker SKlearn Custom Script.ipynb # Jupyter Notebook to run experiments
├── train.csv                                         # Original dataset
├── train-V-1.csv                                     # Training split
├── test-V-1.csv                                      # Testing split
├── requirements.txt                                  # Python dependencies
├── .gitignore                                        # Ignored files (env, vscode, etc.)
└── myenv/                                            # Local virtual environment (ignored)
```

---

## ⚙️ Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/sagemaker-sklearn-example.git
   cd sagemaker-sklearn-example
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv myenv
   source myenv/bin/activate        # (Linux/Mac)
   myenv\Scripts\activate           # (Windows)
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

---

## 📊 Data Preparation

The original dataset is stored in `train.csv`.

It is divided into:
- `train-V-1.csv` → Training set
- `test-V-1.csv` → Testing set

This ensures proper model evaluation and avoids overfitting.

---

## 🧑‍💻 Training with SageMaker

### `script.py`
Contains the custom SKLearn training code that:
- Defines data loading, preprocessing, model training, and evaluation
- Handles SageMaker's input/output conventions
- Saves the trained model for deployment

### Notebook
The Jupyter notebook walks through:
- Uploading datasets to S3
- Creating an SKLearn estimator
- Running training jobs using `script.py`
- Deploying the model as an endpoint

### Sample SageMaker Estimator Code
```python
from sagemaker.sklearn.estimator import SKLearn

sklearn_estimator = SKLearn(
    entry_point="script.py",
    framework_version="1.0-1",
    instance_type="ml.m5.large",
    role=role,
    sagemaker_session=sagemaker_session
)

sklearn_estimator.fit({"train": train_input, "test": test_input})
```

---

## 🖥️ Running Locally

You can also run the training script locally for testing:
```bash
python script.py --train train-V-1.csv --test test-V-1.csv
```

---

## ✅ Results

- Model performance metrics are logged during training
- Trained models can be deployed as SageMaker endpoints for inference
- Model artifacts are saved automatically for later use

---

## 📌 Notes

- `.gitignore` excludes `myenv/`, `.vscode/`, and data files you don't want in Git
- Replace the dataset with your own for real-world use cases
- Update `requirements.txt` as you add new dependencies
- Ensure your AWS credentials are configured for SageMaker access

---

## 🔧 Prerequisites

- AWS Account with SageMaker access
- Python 3.7+
- Configured AWS CLI or IAM role for SageMaker

---

## 📜 License

This project is for educational purposes. You are free to use and modify it.

---

## 🤝 Contributing

Feel free to submit issues and enhancement requests!
