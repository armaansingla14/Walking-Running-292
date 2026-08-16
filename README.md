# 🚶🤸 Walking vs. Jumping Classifier

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![PyQt5](https://img.shields.io/badge/GUI-PyQt5-41CD52?logo=qt&logoColor=white)
![HDF5](https://img.shields.io/badge/Storage-HDF5-0298c3)

A machine-learning project that classifies human motion as **walking** or **jumping** from smartphone accelerometer data. It covers the full pipeline — raw sensor collection, HDF5 storage, signal preprocessing, feature engineering, model training, and a **desktop app** that predicts on new recordings.

🎥 **Demo:** https://youtu.be/yd7NedTEr9g

---

## 🧠 How It Works

```
Phone accelerometer CSVs ──▶ HDF5 store ──▶ preprocess ──▶ features ──▶ classifier ──▶ Walking / Jumping
```

1. **Collect** — three-axis linear-acceleration data is recorded on a phone (in pocket, hand, and backpack positions) for both walking and jumping.
2. **Store** — [`dataintohdf5.py`](dataintohdf5.py) consolidates the raw CSVs into a single **HDF5** dataset (`dataset.hdf5`) organized by member → activity.
3. **Preprocess** — [`processor.py`](processor.py) fills gaps via interpolation and smooths each axis with a moving-average filter.
4. **Feature engineering** — [`feature_extract_norm.py`](feature_extract_norm.py) segments the signal into windows and extracts per-axis statistics (mean, std, min, max, range, median, variance, skewness, kurtosis, RMS), then normalizes them.
5. **Train** — [`train_test_model.py`](train_test_model.py) trains a classifier and saves it to `model.pkl` (with the fitted scaler in `scaler.pkl`).
6. **Predict** — [`desktop-app.py`](desktop-app.py), a PyQt5 GUI, loads a CSV, splits it into 5-second windows, and labels each as **Walking** or **Jumping**.

Signals can be explored visually with [`Data_visulization.py`](Data_visulization.py).

---

## 🛠️ Tech Stack

- **Python** · **NumPy** · **Pandas**
- **scikit-learn** (classification + scaling)
- **SciPy** (skewness / kurtosis features)
- **Matplotlib** (visualization)
- **PyQt5** (desktop GUI)
- **h5py** (HDF5 storage)

---

## 🗂️ Project Structure

```
├── raw-data/                # Raw accelerometer CSVs (walking & jumping, multiple carry positions)
├── dataset.hdf5             # Consolidated HDF5 dataset
├── dataintohdf5.py          # CSV → HDF5 loader
├── processor.py             # Interpolation + moving-average smoothing
├── feature_extract_norm.py  # Windowing, feature extraction & normalization
├── train_test_model.py      # Model training / evaluation
├── model.pkl                # Trained classifier
├── scaler.pkl               # Fitted feature scaler
├── Data_visulization.py     # Signal visualization
└── desktop-app.py           # PyQt5 prediction GUI
```

---

## 🚀 How to Run

```bash
# 1. Build the HDF5 dataset from raw CSVs
python dataintohdf5.py

# 2. (optional) Visualize raw signals
python Data_visulization.py

# 3. Train the model
python train_test_model.py

# 4. Launch the desktop classifier
python desktop-app.py
```

In the app, load a CSV of accelerometer readings and it will classify each 5-second window as **Walking** or **Jumping**.

---

## 👤 Author

**Armaan Singla** — Computer Engineering @ Queen's University
[GitHub](https://github.com/armaansingla14)
