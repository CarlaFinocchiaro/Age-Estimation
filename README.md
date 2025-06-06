# 🗣️ Age Estimation by Voice

This project focuses on estimating a speaker’s age from audio recordings using machine learning. By extracting both acoustic and linguistic features from raw audio, we trained and evaluated several regression models to predict the speaker's age.

## 📁 Dataset

We used a dataset consisting of:

- **Development set**: 2,933 audio recordings, each with 20 pre-extracted features and age labels.
- **Evaluation set**: 691 recordings, same features, but without age labels.

All audio files had the same sampling rate but varied in duration.

## 🎯 Objective

Build a regression model to predict the speaker’s age based on a variety of extracted features from their voice.

## 🧪 Features Extracted

- **Acoustic Features**:
  - MFCCs (13 coefficients, averaged)
  - Pitch range
  - Spectral rolloff (mean and std)
  - Spectral bandwidth (mean and std)
  - Energy, jitter, shimmer
  - Harmonic-to-noise ratio (hnr)
  - Zero-crossing rate
  - Mel spectrogram

- **Linguistic / Temporal Features**:
  - Speaking rate (words/sec)
  - Number of pauses and silence duration
  - Word and character counts

## ⚙️ Preprocessing

- Fixed mislabeled gender values and applied label encoding.
- Removed constant features (e.g., identical sample rate).
- Scaled numerical features for linear models.
- Split data into 80% train / 20% test sets.

## 📈 Models Tested

| Model                       | RMSE     |
|----------------------------|----------|
| Linear Regression          | 10.139   |
| Ridge Regression           | 10.138   |
| K-Nearest Neighbors        | 12.028   |
| Random Forest Regressor    | 9.824    |
| Extra Trees Regressor      | **9.770** |

After hyperparameter tuning, Extra Trees showed the best performance and was used to label the evaluation set.

## 🔍 Hyperparameter Tuning

Grid search with 5-fold cross-validation was performed on:

- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `max_features`
- `bootstrap`

## 🏆 Final Results

- **Extra Trees (best config)**: RMSE ≈ **9.616** on the public leaderboard
- **Random Forest**: RMSE ≈ 9.855

Extra Trees demonstrated better generalization, especially for younger speakers (most represented in the dataset).

## 📌 Future Improvements

- Apply PCA to MFCC and delta features
- Integrate deep features using VGGish embeddings
- Balance dataset or use weighted loss to handle age skew

## 🛠️ Tech Stack

- Python 3
- Librosa
- Scikit-learn
- NumPy, Pandas, Matplotlib

## 👥 Authors

- Alice Banaudi — [LinkedIn](https://www.linkedin.com/in/alicebanaudi)
- Carla Finocchiaro — [LinkedIn](https://www.linkedin.com/in/carla-finocchiaro-3747a5271/)

## 📄 License

This project is for academic purposes only and does not use any proprietary or restricted datasets or models.
