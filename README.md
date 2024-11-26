
# Cryptocurrency Quantum Trading Algorithm

This project implements a cryptocurrency trading system that leverages quantum machine learning (QML) to predict and trade on Bitcoin (BTC) and Ethereum (ETH) based on historical data. The system comprises several Python scripts that handle data collection, preprocessing, model training, evaluation, and real-time backtesting. Below is a detailed description of the system's structure and the functionality of each script.

## Directory Structure


cryptocurrency-quantum-trading/
│
├── data/
│   ├── BTC_daily_data.csv
│   ├── ETH_daily_data.csv
│   └── ...
│
├── data/preprocessed/
│   ├── BTC_preprocessed.csv
│   ├── ETH_preprocessed.csv
│   └── ...
│
├── data/preprocessed_backtesting/
│   ├── BTC_preprocessed_backtesting.csv
│   ├── ETH_preprocessed_backtesting.csv
│   └── ...
│
├── models/
│   ├── BTC_QuantumSVM_model.pkl
│   ├── ETH_QuantumSVM_model.pkl
│   └── ...
│
├── data_collection.py
├── data_preprocessing.py
├── model_training.py
├── model_evaluation.py
├── preprocessed_backtest_data.py
├── realtime_backtester.py
└── README.md
```

## Scripts Overview

### 1. `data_collection.py`
This script fetches historical cryptocurrency data from the CryptoCompare API and saves it into CSV files. It retrieves daily price information for the specified cryptocurrencies (currently Bitcoin, BTC).

#### Key Functions:
- `fetch_data`: Fetches daily price data for a given cryptocurrency.
- `save_data`: Saves the fetched data to CSV files.
- `main`: Loops through a list of cryptocurrencies and fetches data for each.

```python
def fetch_data(coin, limit=2000, aggregate=1):
    # Fetch data from CryptoCompare API
    ...
```

### 2. `data_preprocessing.py`
This script cleans the raw data collected by `data_collection.py` and computes technical indicators like Simple Moving Average (SMA), Exponential Moving Average (EMA), Moving Average Convergence Divergence (MACD), and Relative Strength Index (RSI). It normalizes the features and prepares the data for machine learning models.

#### Key Functions:
- `load_data`: Loads the cryptocurrency data from a CSV file.
- `clean_and_feature_engineer`: Handles data cleaning and calculates technical indicators.
- `save_preprocessed_data`: Saves the preprocessed data into a separate folder.

```python
def clean_and_feature_engineer(data):
    # Clean and calculate technical indicators
    ...
```

### 3. `model_training.py`
This script trains a quantum machine learning model using Quantum Support Vector Classifier (QSVC) from Qiskit. It uses a fidelity-based quantum kernel with a ZZ feature map to classify price movements (up or down) based on the technical indicators.

#### Key Functions:
- `prepare_data`: Prepares the data by splitting it into training and testing datasets.
- `train_quantum_model`: Trains a QSVC model using the training data.
- `evaluate_model`: Evaluates the trained model on the testing data.
- `main`: Orchestrates the training and evaluation of the quantum model.

```python
def train_quantum_model(X_train, y_train, feature_dim):
    # Train QuantumSVM model using Qiskit
    ...
```

### 4. `model_evaluation.py`
This script loads a pre-trained quantum model and evaluates its performance on a separate test dataset. It reports the accuracy and classification results of the model.

#### Key Functions:
- `evaluate_model`: Evaluates the model using accuracy and classification report metrics.
- `main`: Loads the model and dataset, and performs evaluation.

```python
def evaluate_model(model, X, y, X_train, y_train, model_name="QuantumSVM"):
    # Evaluate the model using test data
    ...
```

### 5. `preprocessed_backtest_data.py`
This script preprocesses historical data specifically for backtesting purposes. It handles the cleaning and feature engineering for backtesting, including the calculation of technical indicators and normalization of the features, while excluding the 'close' price from normalization.

#### Key Functions:
- `clean_and_feature_engineer_for_backtesting`: Prepares the data for backtesting by calculating technical indicators and normalizing the data.
- `save_preprocessed_data_for_backtesting`: Saves the preprocessed data specifically for backtesting.

```python
def clean_and_feature_engineer_for_backtesting(data):
    # Preprocess data for backtesting
    ...
```

### 6. `realtime_backtester.py`
This script performs real-time backtesting by fetching minute-level cryptocurrency data from the CryptoCompare API and simulating trades based on the trained quantum model. It handles transaction fees and keeps track of trades in a CSV file.

#### Key Features:
- Fetches minute-level price data.
- Simulates real-time trading decisions using the trained quantum model.
- Logs trades and transaction details (including fees).

```python
class CustomFidelityQuantumKernel(FidelityQuantumKernel):
    # Custom implementation of quantum kernel for real-time backtesting
    ...
```

## How to Use

### Step 1: Data Collection
Run `data_collection.py` to fetch the latest cryptocurrency data.

```bash
python data_collection.py
```

This will fetch data for Bitcoin (BTC) and save it as CSV files in the `data/` directory.

### Step 2: Data Preprocessing
Run `data_preprocessing.py` to clean and preprocess the data, calculating technical indicators and normalizing the features.

```bash
python data_preprocessing.py
```

This will generate preprocessed data and save it in the `data/preprocessed/` directory.

### Step 3: Model Training
Run `model_training.py` to train the QuantumSVM model using the preprocessed data.

```bash
python model_training.py
```

This will train a quantum machine learning model and save it in the `models/` directory.

### Step 4: Model Evaluation
Run `model_evaluation.py` to evaluate the performance of the trained model.

```bash
python model_evaluation.py
```

### Step 5: Backtesting
Run `preprocessed_backtest_data.py` to preprocess data for backtesting and simulate trading.

```bash
python preprocessed_backtest_data.py
```

For real-time backtesting, run `realtime_backtester.py` to simulate real-time trading decisions.

```bash
python realtime_backtester.py
```

## Requirements

- Python 3.x
- Qiskit
- Scikit-learn
- Pandas
- NumPy
- Requests

You can install the required dependencies using `pip`:

```bash
pip install qiskit scikit-learn pandas numpy requests
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

This readme is detailed and includes information about the purpose of each script, key functions, how to use them, and the necessary requirements. It should be suitable for use in the markdown file. Let me know if you need any further adjustments!
