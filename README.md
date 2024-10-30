# DSA4262 - Prediction of m6A RNA modifications from direct RNA-Seq data

This project aims to identify m6A RNA modifications from direct RNA sequencing data by leveraging on XGBoost and feature engineering.

The project structure is as follows.

```bash
main/
├── clustering/                    # Pickle files for clustering
├── model/
│   ├── predict.py                     # Script for making predictions
│   ├── train.py                       # Script for training the model
│   ├── utils.py                       # Script containing functions used for training and prediction
├── notebooks/                     # Notebooks for testing
├── data/
│   ├── sample_rna_data.json       # Sample data for testing the prediction script
├── outputs/
│   ├── model_predictions/         # Csv files containing model prediction outputs
├── .gitignore
├── README.md                      # Project documentation
├── model.joblib                   # Joblib file for pretrained model
└── requirements.txt               # Project dependencies
```


# Table of Contents
- **[Installation](#installation)**<br>
- **[Running the Model](#running-the-model)**<br>
  - **[Model Training](#model-training)**<br>
  - **[Model Prediction](#model-prediction)**<br>
- **[Testing the Prediction Script](#testing-the-prediction-script)**<br>

# Installation
It is recommended to use [Python version 3.8](https://www.python.org). (Python 3.8 is the Default Python Version on Ubuntu 20.04)

To install default Python3 version in Ubuntu 20.04: (If Not Already Installed)
```bash
sudo apt update -y && sudo apt upgrade -y # Recommended to update the system packages to their latest versions available
sudo apt install python3 -y # Install the default Python3 version
python3 -V # Check if Python3 version is installed successfully
```

## If Running on Local Machine:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/m6A-modification-prediction.git
   cd m6A-modification-prediction
   ```

2. **Create Virtual Environment:** (Optional but Recommended)
   ```bash
   python -m venv env
   source env/bin/activate
   ```
   
3. **Install Required Packages:**
   ```bash
   pip install -r requirements.txt
   ```

## If Running on Ubuntu:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/m6A-modification-prediction.git
   cd m6A-modification-prediction
   ```
   
2. **Install pip:** (If Not Already Installed)
   ```bash
   sudo apt install python3-pip
   ```

3. **Install Required Packages:**
   ```bash
   pip install -r requirements.txt
   ```

# Running the Model

## Model Training

To train the model on RNA-Seq data:
```bash
# On Local Machine
python model/train.py --data path/to/rna_data.json --labels path/to/labels_data.info --output_path path/to/save_model.joblib

# On Ubuntu
python3 model/train.py --data path/to/rna_data.json --labels path/to/labels_data.info --output_path path/to/save_model.joblib
```
**Arguments:**
* ``--data``: Path to RNA-seq data, processed by m6Anet, in JSON format.
* ``--labels``: Path to the m6A labels file.
* ``--output_path``: Path to save the trained model file.

The trained model will be saved to the specified path in .joblib format for later use in predictions.

## Model Prediction

To run prediction on new data using the trained model:
```bash
# On Local Machine
python3 model/predict.py --data path/to/new_rna_data.json --model path/to/save_model.joblib --output_path path/to/predictions.csv

# On Ubuntu
python3 model/predict.py --data path/to/new_rna_data.json --model path/to/save_model.joblib --output_path path/to/predictions.csv
```
**Arguments:**
* ``--data``: Path to RNA-seq data, processed by m6Anet, in JSON format.
* ``--model``: Path to the trained model file.
* ``--output_path``: Path to save the prediction results to csv.

# Testing the Prediction Script

- A sample dataset is included in data/sample_rna_data.json for testing the prediction script.
- A pre-trained model is also included in model.joblib.

To run prediction on the sample json file:
```bash
# On Local Machine
python model/predict.py --data data/sample_rna_data.json --model model.joblib --output_path outputs/model_predictions/sample_predictions.json

# On Ubuntu
python3 model/predict.py --data data/sample_rna_data.json --model model.joblib --output_path outputs/model_predictions/sample_predictions.json
```

