# AI-Powered Real-Time Noise Cancellation Adaptive System

Google Colab Stage A pipeline for the FYP classifier.

This repository prepares a three-class audio classifier:

- `0` Clean Speech
- `1` Environmental Noise
- `2` Noisy Speech

The model uses standardized 16 kHz mono audio windows of 2 seconds and mel-spectrogram features. Adaptive noise cancellation, real-time microphone processing, multiple-speaker processing, and audio reconstruction are reserved for the later MATLAB R2022 stage.

## Open directly in Google Colab

After pushing this repository to GitHub, replace `YOUR_USERNAME` with your GitHub username and open:

```text
https://colab.research.google.com/github/YOUR_USERNAME/AI-Powered-Real-Time-Noise-Cancellation-FYP/blob/main/AI_Powered_Real_Time_Noise_Cancellation_FYP.ipynb
```

The notebook installs its Python dependencies, downloads the selected datasets, and creates persistent experiment artifacts. In Colab, run the cells from top to bottom.

## First run

1. Open the notebook in Colab.
2. Keep `QUICK_TEST_MODE = True` for the first run.
3. Run all cells and authorize Google Drive when prompted.
4. Check the final PASS/FAIL report.
5. For final FYP training, change `QUICK_TEST_MODE = False` and use a fresh configuration ID.

Quick-test results validate the pipeline. They are not final performance results.

## Repository layout

```text
.
├── AI_Powered_Real_Time_Noise_Cancellation_FYP.ipynb
├── README.md
├── requirements-colab.txt
├── LICENSES_AND_DATASETS.md
├── .gitignore
├── artifacts/
├── colab/
├── data/
├── docs/
└── matlab/
```

Large raw datasets and generated model files are intentionally not stored in GitHub. The notebook keeps raw audio in temporary Colab storage and saves important manifests, results, checkpoints, plots, model files, and MATLAB configuration files to Google Drive.

## Dataset sources

The default experiment uses Mini LibriSpeech `train-clean-5` for clean speech and ESC-50 for environmental noise. The notebook documents why it does not blindly concatenate Mini LibriSpeech with LibriSpeech `train-clean-100`: overlapping material could cause leakage and inflate evaluation results.

See [LICENSES_AND_DATASETS.md](LICENSES_AND_DATASETS.md) for source links, purpose, license notes, and the limitations of the default experiment.

## What the notebook exports

The successful run creates configuration-specific artifacts including:

- Keras classifier and optional ONNX export
- Class mapping
- Training-only normalization statistics
- Feature and MATLAB preprocessing configuration
- Source and classification manifests
- Training history and plots
- Test predictions, confusion matrix, classification report, and SNR robustness results

The JSON preprocessing contract is the handoff to MATLAB. MATLAB must reproduce the audio windowing, mel extraction, dB conversion, and normalization exactly before real-time integration.
