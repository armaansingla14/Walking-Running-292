# Walking-Running-292

A data-driven project that classifies human motion as either walking or running using smartphone accelerometer data. This project involves data preprocessing, feature extraction, model training, and a simple desktop application interface for real-time prediction.

## 📂 Project Structure

```
├── raw-data/                # Raw CSV files collected from smartphone sensors
├── dataset.hdf5             # Preprocessed HDF5 data
├── datainothdf5.py          # Converts CSV data to HDF5 format
├── Data_visualization.py    # Visualizes accelerometer signals
├── train_test_model.py      # Trains and tests classification models
├── model.pkl                # Trained ML model (saved)
├── scaler.pkl               # Data scaler (normalization)
├── feature_extract_norm.py  # Feature extraction and normalization
├── processor.py             # Pipeline to load, transform, and predict
├── desktop-app.py           # Simple PyQt5 GUI for prediction
└── 292ProjectGroup49.zip    # Final submission package
```

## ⚙️ Technologies Used

- **Python**
- **NumPy**, **Pandas**
- **Scikit-learn**
- **Matplotlib**
- **PyQt5**
- **HDF5 (h5py)**

## 🧠 Workflow

1. **Data Conversion**  
   `datainothdf5.py` converts raw CSVs into an HDF5 format for efficient processing.

2. **Visualization**  
   `Data_visualization.py` helps explore the raw signal patterns.

3. **Feature Engineering**  
   `feature_extract_norm.py` extracts statistical features (mean, variance, etc.) and normalizes the data.

4. **Model Training**  
   `train_test_model.py` trains a classification model and saves it to `model.pkl`.

5. **Prediction App**  
   `desktop-app.py` allows users to make predictions on new data through a simple GUI.

## 🚀 How to Run

```bash
# Convert CSV data to HDF5
python datainothdf5.py

# Visualize raw signals (optional)
python Data_visualization.py

# Train model
python train_test_model.py

# Launch desktop app
python desktop-app.py
```

## 📈 Output

The model classifies movement as:
- **Walking**
- **Running**

Predictions are based on windowed segments of accelerometer readings.

## 👤 Author

Armaan Singla  
Computer Engineering @ Queen's University  
[GitHub Profile](https://github.com/armaansingla14)
